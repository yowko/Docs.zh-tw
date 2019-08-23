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
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921241"
---
# <a name="configuration-element"></a>\<configuration > 元素

通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。

**\<configuration>**

## <a name="syntax"></a>語法

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>屬性

無

## <a name="parent-element"></a>父項目

無

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [ **\<assemblyBinding>** ](assemblybinding-element-for-configuration.md) | 指定位於組態層級的組件繫結原則。|
| [啟動 > 設定架構 **\<** ](./startup/index.md) | 啟動設定架構中的所有元素。 |
| [執行時間 > 設定架構 **\<** ](./runtime/index.md) | 執行時間設定架構中的所有元素。 |
| [system.web > 設定架構 **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | 遠端設定架構中的所有元素。 |
| [系統 .net > 設定架構 **\<** ](./network/index.md) | 網路設定架構中的所有元素。 |
| [cryptographySettings > 設定架構 **\<** ](./cryptography/index.md) | 加密設定架構中的所有元素。 |
| [configuration > 區段架構 **\<** ](configuration-sections-schema.md) | Configuration 區段設定架構中的所有元素。 |
| [追蹤和偵錯設定結構描述](./trace-debug/index.md) | 追蹤和 debug 設定架構中的所有元素。 |
| [ASP.NET 設定架構](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | ASP.NET 設定架構中的所有元素, 包括用於設定 ASP.NET 網站和應用程式的元素。 用於 web.config檔案中。 |
| [webServices > 設定架構 **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Web 服務設定架構中的所有元素。 |
| [Web 設定結構描述](./web/index.md) | Web 設定結構描述中的所有項目，包括用來設定 ASP.NET 如何配合主機應用程式 (例如 IIS) 運作的項目。 用於*aspnet .config*檔案。 |

## <a name="remarks"></a>備註

每個組態檔必須剛好包含一個 **\<組態>** 項目。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
