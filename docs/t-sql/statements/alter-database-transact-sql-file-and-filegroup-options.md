---
title: "ALTER DATABASE 文件和文件组选项 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ADD FILE
- ADD_FILE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting files
- removing files
- deleting filegroups
- file modifications [SQL Server]
- databases [SQL Server], size
- relocating files
- databases [SQL Server], modifying
- file additions [SQL Server], ALTER DATABASE
- file moving [SQL Server]
- default filegroups
- ALTER DATABASE statement, files and filegroups
- initializing files [SQL Server]
- database files [SQL Server]
- moving files
- filegroups [SQL Server], deleting
- adding filegroups
- adding files
- database filegroups [SQL Server]
- adding log files
- modifying files
- filegroups [SQL Server], adding
- file initialization [SQL Server]
- files [SQL Server], deleting
- files [SQL Server], adding
- databases [SQL Server], moving
ms.assetid: 1f635762-f7aa-4241-9b7a-b51b22292b07
caps.latest.revision: 61
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fdd1f2aaab4e4aeeced6eb069255adba5b333abf
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-transact-sql-file-and-filegroup-options"></a>ALTER DATABASE (Transact SQL) 文件和文件组选项 
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中修改与数据库关联的文件和文件组。 添加或从数据库中删除文件和文件组，并更改数据库或其文件和文件组的属性。 有关其他 ALTER DATABASE 选项，请参阅[ALTER DATABASE &#40;Transact SQL &#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
ALTER DATABASE database_name   
{  
    <add_or_modify_files>  
  | <add_or_modify_filegroups>  
}  
[;]  
  
<add_or_modify_files>::=  
{  
    ADD FILE <filespec> [ ,...n ]   
        [ TO FILEGROUP { filegroup_name } ]  
  | ADD LOG FILE <filespec> [ ,...n ]   
  | REMOVE FILE logical_file_name   
  | MODIFY FILE <filespec>  
}  
  
<filespec>::=   
(  
    NAME = logical_file_name    
    [ , NEWNAME = new_logical_name ]   
    [ , FILENAME = {'os_file_name' | 'filestream_path' | 'memory_optimized_data_path' } ]   
    [ , SIZE = size [ KB | MB | GB | TB ] ]   
    [ , MAXSIZE = { max_size [ KB | MB | GB | TB ] | UNLIMITED } ]   
    [ , FILEGROWTH = growth_increment [ KB | MB | GB | TB| % ] ]   
    [ , OFFLINE ]  
)   
  
<add_or_modify_filegroups>::=  
{  
    | ADD FILEGROUP filegroup_name   
        [ CONTAINS FILESTREAM | CONTAINS MEMORY_OPTIMIZED_DATA ]  
    | REMOVE FILEGROUP filegroup_name   
    | MODIFY FILEGROUP filegroup_name  
        { <filegroup_updatability_option>  
        | DEFAULT  
        | NAME = new_filegroup_name   
        | { AUTOGROW_SINGLE_FILE | AUTOGROW_ALL_FILES }  
        }  
}  
<filegroup_updatability_option>::=  
{  
    { READONLY | READWRITE }   
    | { READ_ONLY | READ_WRITE }  
}  
  
```  
  
## <a name="arguments"></a>参数  
**\<add_or_modify_files >:: =**
  
 指定要添加、删除或修改的文件。  
  
 *database_name*  
 要修改的数据库的名称。  
  
 ADD FILE  
 向数据库中添加文件。  
  
 到文件组 { *filegroup_name* }  
 指定要将指定文件添加到的文件组。 若要显示当前的文件组和组是当前的默认设置，请使用[sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)目录视图。  
  
 ADD LOG FILE  
 将要添加的日志文件添加到指定的数据库。  
  
 REMOVE FILE *logical_file_name*  
 从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例中删除逻辑文件说明并删除物理文件。 除非文件为空，否则无法删除文件。  
  
 *logical_file_name*  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中引用文件时所用的逻辑名称。  
  
> [!WARNING]  
>  删除具有 FILE_SNAPSHOT 的数据库文件将成功与之关联的备份，但不是将删除任何关联的快照以避免导致失效引用数据库的文件的备份。 文件将被截断，但将不会以物理方式删除以保留 FILE_SNAPSHOT 的备份不变。 有关详细信息，请参阅 [使用 Microsoft Azure Blob 存储服务进行 SQL Server 备份和还原](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。 **适用于**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]通过[当前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658)。  
  
 MODIFY FILE  
 指定应修改的文件。 只有一个\<filespec > 可以一次更改属性。 名称必须始终指定\<filespec > 来确定要修改的文件。 如果指定了 SIZE，那么新大小必须比文件当前大小要大。  
  
 若要修改数据文件或日志文件的逻辑名称，请在 `NAME` 子句中指定要重命名的逻辑文件名称，并在 `NEWNAME` 子句中指定文件的新逻辑名称。 例如：  
  
```  
MODIFY FILE ( NAME = logical_file_name, NEWNAME = new_logical_name )   
```  
  
 若要将数据文件或日志文件移至新位置，请在 `NAME` 子句中指定当前的逻辑文件名称，并在 `FILENAME` 子句中指定新路径和操作系统文件名称。 例如：  
  
```  
MODIFY FILE ( NAME = logical_file_name, FILENAME = ' new_path/os_file_name ' )  
```  
  
 在移动全文目录时，请只在 FILENAME 子句中指定新路径。 请不要指定操作系统文件名称。  
  
 有关详细信息，请参阅[移动数据库文件](../../relational-databases/databases/move-database-files.md)。  
  
 对于 FILESTREAM 文件组，可以联机修改 NAME。 可以联机修改 FILENAME；但是，只有在实际重新分配容器且关闭并重新启动服务器之后，所做的更改才生效。  
  
 可以将 FILESTREAM 文件设置为 OFFLINE。 在 FILESTREAM 文件处于脱机状态时，它的父文件组将在内部标记为脱机；因此，针对该文件组内 FILESTREAM 数据的所有访问均将失败。  
  
> [!NOTE]  
>  \<add_or_modify_files > 选项将不可用在包含数据库中。
  
 **\<filespec >:: =**  
  
 控制文件属性。  
  
 名称*logical_file_name*  
 指定文件的逻辑名称。  
  
 *logical_file_name*  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例中引用文件时所用的逻辑名称。  
  
 NEWNAME *new_logical_file_name*  
 指定文件的新逻辑名称。  
  
 *new_logical_file_name*  
 用于替换现有逻辑文件名称的名称。 名称必须在数据库中是唯一且符合规则[标识符](../../relational-databases/databases/database-identifiers.md)。 该名称可以是字符或 Unicode 常量、常规标识符或分隔标识符。  
  
 FILENAME { *os_file_name* | *filestream_path*  | *memory_optimized_data_path*}  
 指定操作系统（物理）文件名称。  
  
 *os_file_name*  
 对于标准 (ROWS) 文件组，这是在创建文件时操作系统所使用的路径和文件名。 该文件必须驻留在安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的服务器上。 在执行 ALTER DATABASE 语句前，指定的路径必须已经存在。  
  
 如果为该文件指定了 UNC 路径，则无法设置 SIZE、MAXSIZE 和 FILEGROWTH 参数。  
  
> [!NOTE]  
>  系统数据库不能位于 UNC 共享目录中。  
  
 不应将数据文件放在压缩文件系统中，除非这些文件是只读辅助文件或该数据库是只读的。 日志文件一定不要放在压缩文件系统中。  
  
 如果此文件位于原始分区， *os_file_name*必须指定现有的原始分区的驱动器号。 每个原始分区上只能存放一个文件。  
  
  *filestream_path*   
 对于 FILESTREAM 文件组，FILENAME 指向将存储 FILESTREAM 数据的路径。 在最后一个文件夹之前的路径必须存在，但不能存在最后一个文件夹。 例如，如果指定路径 C:\MyFiles\MyFilestreamData、C:\MyFiles 必须存在才能运行 ALTER DATABASE，但 MyFilestreamData 文件夹不能存在。  
  
 SIZE 和 FILEGROWTH 属性不适用于 FILESTREAM 文件组。  
  
  *memory_optimized_data_path*   
 对于内存优化文件组，文FILENAME 会引用将存储内存优化数据的路径。 在最后一个文件夹之前的路径必须存在，但不能存在最后一个文件夹。 例如，如果指定路径 C:\MyFiles\MyData、C:\MyFiles 必须存在才能运行 ALTER DATABASE，但 MyData 文件夹不能存在。  
  
 必须在同一语句中创建文件组和文件 (`<filespec>`)。  
  
 SIZE、MAXSIZE 和 FILEGROWTH 属性不适用于内存优化文件组。  
  
 大小*大小*  
 指定文件大小。 大小不适用于 FILESTREAM 文件组。  
  
 *大小*  
 是该文件的大小。  
  
 如果使用添加文件时，指定*大小*文件的初始大小。 如果修改文件后，指定*大小*是新的大小的文件，并且必须是大于当前的文件大小。  
  
 当*大小*对于主文件中，未提供[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用中的主文件的大小**模型**数据库。 当指定了辅助数据文件或日志文件但*大小*没有为文件中，指定[!INCLUDE[ssDE](../../includes/ssde-md.md)]使文件成为 1 MB。  
  
 后缀 KB、MB、GB 和 TB 可用于指定千字节、兆字节、千兆字节或兆兆字节。 默认值为 MB。 指定整数，不包含小数。 若要指定兆字节的分数，请通过将数字乘以 1024 将该值转换为千字节。 例如，应指定 1536 KB 而不是 1.5MB (1.5 x 1024 = 1536)。  
  
 MAXSIZE { *max_size*|不限}  
 指定文件可增大到的最大文件大小。  
  
 *max_size*  
 最大的文件大小。 后缀 KB、MB、GB 和 TB 可用于指定千字节、兆字节、千兆字节或兆兆字节。 默认值为 MB。 指定整数，不包含小数。 如果*max_size*未指定，则将增加文件大小，直到磁盘已满。  
  
 UNLIMITED  
 指定文件将增长到磁盘充满。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，指定为不限制增长的日志文件的最大大小为 2 TB，而数据文件的最大大小为 16 TB。 为 FILESTREAM 容器指定此选项时，没有最大大小。 它将继续增大，直到磁盘已满。  
  
 FILEGROWTH *growth_increment*  
 指定文件的自动增量。 文件的 FILEGROWTH 设置不能超过 MAXSIZE 设置。 FILEGROWTH 不适用于 FILESTREAM 文件组。  
  
 *growth_increment*  
 每次需要新空间时为文件添加的空间量。  
  
 该值可以 MB、KB、GB、TB 或百分比 (%) 为单位指定。 如果未在数量后面指定 MB、KB 或 %，则默认值为 MB。 如果指定 %，则增量大小为发生增长时文件大小的指定百分比。 指定的大小舍入为最接近的 64 KB 的倍数。  
  
 如果值为 0，则表明自动增长被设置为关闭，且不允许增加空间。  
  
 如果未指定 FILEGROWTH，默认值是：  
  
|版本|默认值|  
|-------------|--------------------|  
|开始[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|数据 64 MB。 日志文件 64 MB。|  
|开始[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|数据 1 MB。 10%的日志文件。|  
|之前[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|数据 10%。 10%的日志文件。|  
  
 OFFLINE  
 将文件设置为脱机并使文件组中的所有对象都不可访问。  
  
> [!CAUTION]  
>  仅当文件已损坏但可以还原时，才能使用该选项。 对于设置为 OFFLINE 的文件，只有通过从备份中还原该文件，才能将其设置为联机。 有关还原单个文件的详细信息，请参阅 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)。  
  
> [!NOTE]  
>  \<filespec > 选项将不可用在包含数据库中。  
  
 **\<add_or_modify_filegroups >:: =**  
  
 在数据库中添加、修改或删除文件组。  
  
 添加文件组*filegroup_name*  
 向数据库中添加文件组。  
  
 CONTAINS FILESTREAM  
 指定文件组在文件系统中存储 FILESTREAM 二进制大型对象 (BLOB)。  
  
 CONTAINS MEMORY_OPTIMIZED_DATA  

**适用于**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]通过[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 指定文件组在文件系统中存储内存优化数据。 有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。 每个数据库只能有一个 MEMORY_OPTIMIZED_DATA 文件组。 在创建内存优化表时，文件组不能为空。 其中必须至少包含一个文件。 *filegroup_name*指向的路径。 在最后一个文件夹之前的路径必须存在，但不能存在最后一个文件夹。  
  
 下面的示例创建添加到一个添加到名为 xtp_db 的数据库的文件组，然后向该文件组添加一个文件。 该文件组存储 memory_optimized 数据。  
  
```  
ALTER DATABASE xtp_db ADD FILEGROUP xtp_fg CONTAINS MEMORY_OPTIMIZED_DATA;  
GO  
ALTER DATABASE xtp_db ADD FILE (NAME='xtp_mod', FILENAME='d:\data\xtp_mod') TO FILEGROUP xtp_fg;  
```  
  
 删除文件组*filegroup_name*  
 从数据库中删除文件组。 除非文件组为空，否则无法将其删除。 首先从文件组中删除所有文件。 有关详细信息，请参阅"删除文件*logical_file_name*，"本主题前面的。  
  
> [!NOTE]  
>  除非 FILESTREAM 垃圾回收器已从 FILESTREAM 容器中删除所有文件，删除 FILESTREAM 容器的 ALTER DATABASE REMOVE FILE 操作将失败并返回错误。 请参阅本主题后面“备注”中的“删除 FILESTREAM 容器”部分。  
  
修改文件组*filegroup_name* { \<filegroup_updatability_option > |默认 |名称 **=**  *new_filegroup_name* } 通过将状态设置为 READ_ONLY 或 READ_WRITE，使该数据库，默认文件组的文件组中修改该文件组或更改的文件组名称。  
  
 \<filegroup_updatability_option >  
 对文件组设置只读或读/写属性。  
  
 DEFAULT  
 更改默认的数据库文件组到*filegroup_name*。 数据库中只能有一个文件组作为默认文件组。 有关详细信息，请参阅 [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md)。  
  
 名称 = *new_filegroup_name*  
 文件组名称更改为*new_filegroup_name*。  
  
 AUTOGROW_SINGLE_FILE  
**适用于**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]通过[当前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 在文件组中的文件符合自动增长阈值时，仅该文件是增长。 这是默认设置。  
  
 AUTOGROW_ALL_FILES  

**适用于**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]通过[当前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 如果文件组中的文件达到了自动增长阈值，增加的文件组中的所有文件。  
  
 **\<filegroup_updatability_option >:: =**  
  
 对文件组设置只读或读/写属性。  
  
 READ_ONLY | READONLY  
 指定文件组为只读。 不允许更新其中的对象。 主文件组不能设置为只读。 若要更改此状态，您必须对数据库有独占访问权限。 有关详细信息，请参阅 SINGLE_USER 子句。  
  
 因为只读数据库不允许数据修改，所以将发生以下情况：  
  
-   系统启动时，将跳过自动恢复。  
  
-   不能收缩数据库。  
  
-   在只读数据库中不会进行锁定。 这可以加快查询速度。  
  
> [!NOTE]  
>  未来版本中将删除 READONLY 关键字[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 请避免在新的开发工作中使用 READONLY，并计划修改当前使用 READONLY 的应用程序。 Use READ_ONLY instead.  
  
 READ_WRITE | READWRITE   
 将该组指定为 READ_WRITE。 允许更新文件组中的对象。 若要更改此状态，您必须对数据库有独占访问权限。 有关详细信息，请参阅 SINGLE_USER 子句。  
  
> [!NOTE]  
>  未来版本中将删除 READWRITE 关键字[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 避免在新的开发工作中使用 READWRITE，并计划修改当前使用 READWRITE 的应用程序。 请改用 READ_WRITE。  
  
 可以通过检查确定这些选项的状态**is_read_only**中的列**sys.databases**目录视图或**Updateability**属性DATABASEPROPERTYEX 函数。  
  
## <a name="remarks"></a>注释  
 若要减小数据库大小，使用[DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)。  
  
 当 BACKUP 语句正在运行时，不能添加或删除文件。  
  
 可以为每个数据库指定最多 32,767 个文件和 32,767 个文件组。  
  
 在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本中，对数据库文件状态（例如，联机或脱机）的维护是独立于数据库状态的。 有关详细信息，请参阅[文件状态](../../relational-databases/databases/file-states.md)。 文件组中的文件的状态决定整个文件组的可用性。 文件组中的所有文件都必须联机，文件组才可用。 如果文件组脱机，则使用 SQL 语句访问文件组的所有尝试都会失败并报告错误。 在为 SELECT 语句生成查询计划时，查询优化器会避免驻留在脱机文件组中的非聚集索引和索引视图。 这样，这些语句就会成功。 但是，如果脱机文件组包含目标表的堆或聚集索引，SELECT 语句将失败。 此外，如果 INSERT、UPDATE 或 DELETE 语句修改的表的索引包含在脱机文件组中，这些语句将失败。  
  
## <a name="moving-files"></a>移动文件  
 您可通过在 FILENAME 中指定新位置来移动系统或用户定义的数据和日志文件。 这可能会在以下情况下有用：  
  
-   故障恢复。 例如，数据库处于可疑模式或因硬件故障而关闭  
  
-   计划的重定位  
  
-   为预定的磁盘维护操作而进行的重定位  
  
 有关详细信息，请参阅[移动数据库文件](../../relational-databases/databases/move-database-files.md)。  
  
## <a name="initializing-files"></a>初始化文件  
 默认情况下，在执行下列操作之一时，将通过在文件中填充零来初始化数据和日志文件。  
  
-   创建数据库  
  
-   向现有数据库添加文件  
  
-   增加现有文件的大小  
  
-   还原数据库或文件组  
  
 可以在瞬间对数据文件进行初始化。 这样，可以快速执行这些文件操作。  
  
## <a name="removing-a-filestream-container"></a>删除 FILESTREAM 容器  
 即使已使用“DBCC SHRINKFILE”操作清空 FILESTREAM 容器，但出于各种系统维护原因，数据库可能仍然需要保留对已删除文件的引用。 [sp_filestream_force_garbage_collection &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)将运行 FILESTREAM 垃圾回收器删除这些文件时，则可以安全进行这些操作。 除非 FILESTREAM 垃圾回收器已从 FILESTREAM 容器中删除所有文件，否则 ALTER DATABASEREMOVE FILE 操作将无法删除 FILESTREAM 容器并返回错误。 建议使用以下过程删除 FILESTREAM 容器。  
  
1.  运行[DBCC SHRINKFILE &#40;Transact SQL &#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)带有 EMPTYFILE 选项以将此容器的活动内容移动到其他容器。  
  
2.  确保已在 FULL 或 BULK_LOGGED 恢复模型中执行日志备份。  
  
3.  确保复制日志读取器作业已运行（如果相关）。  
  
4.  运行[sp_filestream_force_garbage_collection &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)强制垃圾回收器删除不再需要此容器中的任何文件。  
  
5.  执行带有 REMOVE FILE 选项的 ALTER DATABASE，以删除此容器。  
  
6.  再重复一次步骤 2 到 4，以完成垃圾回收。  
  
7.  使用 ALTER Database...REMOVE FILE 删除此容器。  
  
## <a name="examples"></a>示例  
  
### <a name="a-adding-a-file-to-a-database"></a>A. 向数据库中添加文件  
 以下示例将一个 5 MB 的数据文件添加到 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库。  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD FILE   
(  
    NAME = Test1dat2,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat2.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
);  
GO  
  
```  
  
### <a name="b-adding-a-filegroup-with-two-files-to-a-database"></a>B. 向数据库中添加由两个文件组成的文件组  
 以下示例在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库中创建文件组 `Test1FG1`，然后将两个 5 MB 的文件添加到该文件组。  
  
```  
USE master  
GO  
ALTER DATABASE AdventureWorks2012  
ADD FILEGROUP Test1FG1;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD FILE   
(  
    NAME = test1dat3,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat3.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
),  
(  
    NAME = test1dat4,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat4.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
)  
TO FILEGROUP Test1FG1;  
GO  
  
```  
  
### <a name="c-adding-two-log-files-to-a-database"></a>C. 向数据库中添加两个日志文件  
 下面的示例向 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库中添加两个 5 MB 的日志文件。  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD LOG FILE   
(  
    NAME = test1log2,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\test2log.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
),  
(  
    NAME = test1log3,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\DATA\test3log.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
);  
GO  
  
```  
  
### <a name="d-removing-a-file-from-a-database"></a>D. 从数据库中删除文件  
 以下示例删除示例 B 中添加的一个文件。  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat4;  
GO  
  
```  
  
### <a name="e-modifying-a-file"></a>E. 修改文件  
以下示例增加示例 B 中添加的一个文件的大小。  
 仅，ALTER DATABASE MODIFY FILE 命令与可以使文件大小更大，因此如果你需要使文件大小更小你需要使用 DBCC SHRINKFILE。  
  
```  
USE master;  
GO
  
ALTER DATABASE AdventureWorks2012   
MODIFY FILE  
(NAME = test1dat3,  
SIZE = 200MB);  
GO  
```

此示例中收缩数据文件的大小为 100 MB，然后指定在该数量的大小。 

```
USE AdventureWorks2012;
GO

DBCC SHRINKFILE (AdventureWorks2012_data, 100);
GO

USE master;  
GO
  
ALTER DATABASE AdventureWorks2012   
MODIFY FILE  
(NAME = test1dat3,  
SIZE = 200MB);  
GO
```
 
  
### <a name="f-moving-a-file-to-a-new-location"></a>F. 将文件移至新位置  
 以下示例将在示例 A 中创建的 `Test1dat2` 文件移至新目录中。  
  
> [!NOTE]  
>  必须先将该文件实际移至新目录中，然后才能运行此示例。 然后，停止和启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，或使 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库 OFFLINE 再 ONLINE，以实施更改。  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
MODIFY FILE  
(  
    NAME = Test1dat2,  
    FILENAME = N'c:\t1dat2.ndf'  
);  
GO  
```  
  
### <a name="g-moving-tempdb-to-a-new-location"></a>G. 将 tempdb 移至新位置  
 以下示例将 `tempdb` 从其在磁盘上的当前位置移至另一个磁盘位置。 由于每次启动 MSSQLSERVER 服务时都会重新创建 `tempdb`，因此您不必实际移动数据和日志文件。 在步骤 3 中重新启动服务时，将创建这些文件。 在重新启动该服务之前，`tempdb` 将继续在现有位置发挥作用。  
  
1.  确定 `tempdb` 数据库的逻辑文件名称以及这些文件在磁盘上的当前位置。  
  
    ```  
    SELECT name, physical_name  
    FROM sys.master_files  
    WHERE database_id = DB_ID('tempdb');  
    GO  
    ```  
  
2.  使用 `ALTER DATABASE`更改每个文件的位置。  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = tempdev, FILENAME = 'E:\SQLData\tempdb.mdf');  
    GO  
    ALTER DATABASE  tempdb   
    MODIFY FILE (NAME = templog, FILENAME = 'E:\SQLData\templog.ldf');  
    GO  
    ```  
  
3.  停止再重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。  
  
4.  验证文件更改。  
  
    ```  
    SELECT name, physical_name  
    FROM sys.master_files  
    WHERE database_id = DB_ID('tempdb');  
    ```  
  
5.  将 tempdb.mdf 和 templog.ldf 文件从其原始位置中删除。  
  
### <a name="h-making-a-filegroup-the-default"></a>H. 使文件组成为默认文件组  
 下面的示例使`Test1FG1`示例 B 中的默认文件组创建的文件组。 然后，默认文件组被重置为 `PRIMARY` 文件组。 请注意，必须使用括号或引号分隔 `PRIMARY`。  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
MODIFY FILEGROUP Test1FG1 DEFAULT;  
GO  
ALTER DATABASE AdventureWorks2012   
MODIFY FILEGROUP [PRIMARY] DEFAULT;  
GO  
  
```  
  
### <a name="i-adding-a-filegroup-using-alter-database"></a>I. 使用 ALTER DATABASE 添加文件组  
 以下示例将一个包含 `FILEGROUP` 子句的 `FILESTREAM` 添加到 `FileStreamPhotoDB` 数据库。  
  
```  
--Create and add a FILEGROUP that CONTAINS the FILESTREAM clause to  
--the FileStreamPhotoDB database.  
ALTER DATABASE FileStreamPhotoDB  
ADD FILEGROUP TodaysPhotoShoot  
CONTAINS FILESTREAM;  
GO  
  
--Add a file for storing database photos to FILEGROUP   
ALTER DATABASE FileStreamPhotoDB  
ADD FILE  
(  
    NAME= 'PhotoShoot1',  
    FILENAME = 'C:\Users\Administrator\Pictures\TodaysPhotoShoot.ndf'  
)  
TO FILEGROUP TodaysPhotoShoot;  
GO  
```      
        
### <a name="j-change-filegroup-so-that-when-a-file-in-the-filegroup-meets-the-autogrow-threshold-all-files-in-the-filegroup-grow"></a>J. 更改文件组，以便当文件组中的文件达到了自动增长阈值，文件组中的所有文件都增长
 下面的示例生成所需`ALTER DATABASE`语句来修改与读写文件组`AUTOGROW_ALL_FILES`设置。  
  
```  
--Generate ALTER DATABASE ... MODIFY FILEGROUP statements  
--so that all read-write filegroups grow at the same time.  
SET NOCOUNT ON;

DROP TABLE IF EXISTS #tmpdbs
CREATE TABLE #tmpdbs (id int IDENTITY(1,1), [dbid] int, [dbname] sysname, isdone bit);

DROP TABLE IF EXISTS #tmpfgs
CREATE TABLE #tmpfgs (id int IDENTITY(1,1), [dbid] int, [dbname] sysname, fgname sysname, isdone bit);

INSERT INTO #tmpdbs ([dbid], [dbname], [isdone])
SELECT database_id, name, 0 FROM master.sys.databases (NOLOCK) WHERE is_read_only = 0 AND state = 0;

DECLARE @dbid int, @query VARCHAR(1000), @dbname sysname, @fgname sysname

WHILE (SELECT COUNT(id) FROM #tmpdbs WHERE isdone = 0) > 0
BEGIN
    SELECT TOP 1 @dbname = [dbname], @dbid = [dbid] FROM #tmpdbs WHERE isdone = 0

    SET @query = 'SELECT ' + CAST(@dbid AS NVARCHAR) + ', ''' + @dbname + ''', [name], 0 FROM [' + @dbname + '].sys.filegroups WHERE [type] = ''FG'' AND is_read_only = 0;'
    INSERT INTO #tmpfgs
    EXEC (@query)

    UPDATE #tmpdbs
    SET isdone = 1
    WHERE [dbid] = @dbid
END;

IF (SELECT COUNT(ID) FROM #tmpfgs) > 0
BEGIN
    WHILE (SELECT COUNT(id) FROM #tmpfgs WHERE isdone = 0) > 0
    BEGIN
        SELECT TOP 1 @dbname = [dbname], @dbid = [dbid], @fgname = fgname FROM #tmpfgs WHERE isdone = 0

        SET @query = 'ALTER DATABASE [' + @dbname + '] MODIFY FILEGROUP [' + @fgname + '] AUTOGROW_ALL_FILES;'

        PRINT @query

        UPDATE #tmpfgs
        SET isdone = 1
        WHERE [dbid] = @dbid AND fgname = @fgname
    END
END; 
GO  
```      
  
## <a name="see-also"></a>另请参阅  
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DATABASEPROPERTYEX (Transact-SQL)](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE (Transact SQL)](../../t-sql/statements/drop-database-transact-sql.md)   
 [sp_spaceused (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.data_spaces &#40;Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.filegroups &#40;Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files &#40;Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [二进制大型对象 &#40;Blob&#41; 数据 &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)   
 [DBCC SHRINKFILE (Transact-SQL)](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)   
 [sp_filestream_force_garbage_collection (Transact-SQL)](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)  
  
  
