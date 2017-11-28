---
title: "&lt;linkedConfiguration&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bfea438ec19303c35ad9d7a2816cb7b9473a00c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration > 項目

指定要包含的組態檔。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration >**

## <a name="syntax"></a>語法

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>屬性

|           | 說明 |
| --------- | ----------- |
| **href**  | 必要屬性。<br><br>包含組態檔的 URL。 唯一支援的格式**href**屬性是`file://`。 支援本機檔案及 UNC 檔案。 |

## <a name="parent-element"></a>父項目

|     | 說明 |
| --- | ----------- |
| [**\<assemblyBinding >**項目](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | 指定位於組態層級的組件繫結原則。 |

## <a name="child-elements"></a>子元素

無

## <a name="remarks"></a>備註

**\<LinkedConfiguration >**項目可簡化元件組件的服務。 如果一或多個應用程式使用具有組態檔中的已知位置的組件，可以使用使用組件的應用程式的組態檔 **\<linkedConfiguration >**包含組件組態檔中，而不是直接包含組態資訊的項目。 當已服務元件組件時，更新通用的組態檔提供使用組件的所有應用程式更新的組態資訊。

> [!NOTE]
> **\<LinkedConfiguration >**項目不支援有 Windows-並存資訊清單的應用程式。

下列規則可管理使用連結的組態檔：

- 包含的組態檔中的設定只會影響載入器繫結原則，且僅供載入器。 包含的組態檔可以有繫結原則，以外的設定，但是這些設定不會有任何效果。

- 唯一支援的格式`href`屬性是`file://`。 支援本機檔案及 UNC 檔案。

- 連結的組態，每個組態檔的數目沒有限制。

- 所有連結的組態檔會合併成一個檔案，類似的行為`#include`C/c + + 中的指示詞。

- **\<LinkedConfiguration >**項目只允許在應用程式組態檔，則會忽略在*Machine.config*。

- 已偵測到循環參考，並終止。 也就是說，如果 **\<linkedConfiguration >**的一系列的組態檔項目形成迴圈，會偵測到迴圈，並將其停止。

## <a name="example"></a>範例

下列範例會示範如何包含從本機硬碟的組態檔：

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>請參閱

[**\<assemblyBinding >**項目](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
