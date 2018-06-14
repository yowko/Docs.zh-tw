---
title: 啟動設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 59f0441b79244eb529be338495c32af886a5f2b3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745093"
---
# <a name="startup-settings-schema"></a>啟動設定結構描述
啟動設定會指定應執行應用程式之 Common Language Runtime 的版本。  
  
|項目|描述|  
|-------------|-----------------|  
|[\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|指定應用程式只支援 Common Language Runtime 1.0 版。 使用執行階段版本 1.1 建置的應用程式應該使用 **\<supportedRuntime>** 項目。|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|指定應用程式支援的通用語言執行平台版本。|  
|[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|包含 **\<requiredRuntime>** 和 **\<supportedRuntime>** 項目。|  
  
## <a name="see-also"></a>另請參閱  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> 指定要使用哪一個執行階段版本](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
