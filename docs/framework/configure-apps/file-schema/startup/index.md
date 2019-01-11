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
ms.openlocfilehash: 0a03438968f487f574606f415fb9d43223030038
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222151"
---
# <a name="startup-settings-schema"></a>啟動設定結構描述

啟動設定會指定應執行應用程式之 Common Language Runtime 的版本。  
  
|元素|描述|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|指定應用程式只支援 Common Language Runtime 1.0 版。 使用執行階段版本 1.1 建置的應用程式應該使用 **\<supportedRuntime>** 項目。|  
|[\<supportedRuntime>](supportedruntime-element.md)|指定應用程式支援的通用語言執行平台版本。|  
|[\<startup>](startup-element.md)|包含 **\<requiredRuntime>** 和 **\<supportedRuntime>** 項目。|  
  
## <a name="see-also"></a>另請參閱

- [組態檔結構描述](../index.md)  
- [如何：設定應用程式，以支援.NET Framework 4 或更新版本](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)