---
title: 啟動設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701511"
---
# <a name="startup-settings-schema"></a>啟動設定結構描述

啟動設定會指定應執行應用程式之 Common Language Runtime 的版本。  
  
|元素|描述|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|指定應用程式只支援 Common Language Runtime 1.0 版。 以執行階段版本1.1 建立的應用程式應該使用 **\<supportedRuntime>** 元素。|  
|[\<supportedRuntime>](supportedruntime-element.md)|指定應用程式支援的通用語言執行平台版本。|  
|[\<startup>](startup-element.md)|包含 **\<requiredRuntime>** 和 **\<supportedRuntime>** 元素。|  
  
## <a name="see-also"></a>另請參閱

- [設定檔架構](../index.md)
- [如何：將應用程式設定為支援 .NET Framework 4 或更新版本](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
