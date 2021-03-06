---
title: 附录-1 (OracleToSQL) |Microsoft 文档
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e01f8be5-ce68-4c9f-bd13-d65e73a16470
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 4afeb0ab89e38f9d0b5533bcc56405a0dbdb3cbf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="appendix---1-oracletosql"></a>附录-1 (OracleToSQL)
SSMA 控制台命令行选项的快速视图：  
  
|Sl。 否。|开关|必需？|开关参数|允许的值|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|是|scriptfile|有效的 XML 文件名称。<br /><br />控制台脚本定义文件。|  
|2|-v/变量|否|variablevaluefile|有效的 XML 文件名称。<br /><br />如果脚本文件中使用变量，则必须指定此文件。|  
|3|-c/serverconnection|否|serverconnectionfile|有效的 XML 文件名称。<br /><br />此文件包含服务器连接信息。|  
|4|-x/xmloutput|否|xmloutputfile|此选项指示以 XML 格式的控制台输出。 如果未指定此选项，默认输出是以文本格式。<br /><br />如果未指定 xmloutputfile，XML 输出定向到`STDOUT`。<br /><br />Xmloutputfile 是文件的向其写入控制台输出以 XML 格式的名称。|  
|5|-l/日志|否|logfile|有效的文件名称。|  
|6|-e/projectenvironment|否|projectenvironmentfolder|有效的文件夹名称包含 SSMA 项目环境文件。|  
|7|-p/securepassword|否|-a/添加 {< server_id > [，… n]&#124;所有} – c&#124;serverconnection < 服务器连接文件 > [-v&#124;变量 < 变量值文件 >] [-o/覆盖]<br /><br />或<br /><br />-a/添加 {< server_id > [，… n]&#124;所有} – s&#124;脚本 < 脚本文件 > [-v&#124;变量 < 变量值文件 >] [-o/覆盖]<br /><br />-r/删除 {< server_id > [，… n]&#124;所有}<br /><br />-l/列表<br /><br />– e/导出 {< 服务器 id > [，… n]&#124;所有} < 加密的密码-文件 ><br /><br />– i / 导入 {< 服务器 id > [，… n]&#124;所有} < 加密密码的文件 >|如果指定，此选项必须不能与任何其他选项结合。<br /><br />服务器 id： 为 {字符串} 的服务器提供唯一的 ID<br /><br />服务器连接文件： 服务器定义文件 （serverconnectionfile 或脚本文件）。<br /><br />变量值文件： 它是变量定义文件，并用于服务器连接文件。<br /><br />加密密码文件： 它是使用用户指定通行短语加密 server 密码文件。|  
|8|-?|否|不适用|不适用|  
  
## <a name="see-also"></a>另请参阅  
[执行 SSMA 控制台 (Oracle)](http://msdn.microsoft.com/en-us/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
