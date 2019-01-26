---
title: '&lt;設定&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 92d4a4dacddcce3e3b12337f0c55ff49c3c8e6ae
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084441"
---
# <a name="configuration-element"></a>\<組態 > 項目

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

## <a name="parent-element"></a>父項目

None

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | 指定位於組態層級的組件繫結原則。|
| [**\<啟動 >** 設定結構描述](~/docs/framework/configure-apps/file-schema/startup/index.md) | 啟動設定結構描述中的所有項目。 |
| [**\<執行階段 >** 設定結構描述](~/docs/framework/configure-apps/file-schema/runtime/index.md) | 在執行階段設定結構描述中的所有項目。 |
| [**\<system.runtime.remoting >** 設定結構描述](https://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | 在 遠端設定結構描述中的所有項目。 |
| [**\<system.Net >** 設定結構描述](~/docs/framework/configure-apps/file-schema/network/index.md) | 網路設定結構描述中的所有項目。 |
| [**\<cryptographySettings >** 設定結構描述](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | 密碼編譯設定結構描述中的所有項目。 |
| [**\<組態 >** 區段結構描述](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | 組態區段的設定結構描述中的所有項目。 |
| [追蹤和偵錯設定結構描述](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | 追蹤和偵錯設定結構描述中的所有項目。 |
| [ASP.NET 組態設定結構描述](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx) | ASP.NET 設定結構描述，包括用來設定 ASP.NET 網站和應用程式的項目中的所有項目。 用於*Web.config*檔案。 |
| [**\<webServices>** Settings Schema](https://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | Web 服務設定結構描述中的所有項目。 |
| [Web 設定結構描述](~/docs/framework/configure-apps/file-schema/web/index.md) | Web 設定結構描述中的所有項目，包括用來設定 ASP.NET 如何配合主機應用程式 (例如 IIS) 運作的項目。 用於*aspnet.config*檔案。 |

## <a name="remarks"></a>備註

每個組態檔必須剛好包含一個**\<組態 >** 項目。

## <a name="see-also"></a>另請參閱

- [適用於.NET Framework 的組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
