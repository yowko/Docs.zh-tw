---
title: <configuration> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 8f79981a55d0bc9b1cd522e45f5606fda102c72c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544684"
---
# <a name="configuration-element"></a>\<configuration> 項目

通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。

**\<configuration>**

## <a name="syntax"></a>語法

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>屬性

None

## <a name="parent-element"></a>父元素

None

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | 指定位於組態層級的組件繫結原則。|
| [**\<startup>** 設定架構](./startup/index.md) | 啟動設定架構中的所有元素。 |
| [**\<runtime>** 設定架構](./runtime/index.md) | 執行時間設定架構中的所有元素。 |
| [**\<system.runtime.remoting>** 設定架構](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | 遠端設定架構中的所有元素。 |
| [**\<system.Net>** 設定架構](./network/index.md) | 網路設定架構中的所有元素。 |
| [**\<cryptographySettings>** 設定架構](./cryptography/index.md) | 加密設定架構中的所有元素。 |
| [**\<configuration>** 區段架構](configuration-sections-schema.md) | Configuration 區段設定架構中的所有元素。 |
| [追蹤和調試設定架構](./trace-debug/index.md) | 追蹤和 debug 設定架構中的所有元素。 |
| [ASP.NET 設定架構](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | ASP.NET 設定架構中的所有專案，包括用來設定 ASP.NET 網站和應用程式的元素。 用於 *Web.config* 檔案中。 |
| [**\<webServices>** 設定架構](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Web 服務設定架構中的所有元素。 |
| [Web 設定架構](./web/index.md) | Web 設定結構描述中的所有項目，包括用來設定 ASP.NET 如何配合主機應用程式 (例如 IIS) 運作的項目。 用於 *aspnet.config* 檔案中。 |

## <a name="remarks"></a>備註

每個設定檔都必須只包含一個 **\<configuration>** 元素。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
