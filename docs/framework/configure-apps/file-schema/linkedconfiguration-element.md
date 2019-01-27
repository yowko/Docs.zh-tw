---
title: '&lt;linkedConfiguration&gt;項目'
ms.date: 03/30/2017
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
ms.openlocfilehash: 2fd504fff161caaff147b203ab66cec04a6414ef
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083442"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration > 項目

指定要包含的組態檔。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**

## <a name="syntax"></a>語法

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **href**  | 必要屬性。<br><br>包含組態檔的 URL。 唯一支援的格式**href**屬性是`file://`。 支援本機檔案和 UNC 檔案。 |

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [**\<Assemblybinding> >** 項目](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | 指定位於組態層級的組件繫結原則。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

 **\<LinkedConfiguration >** 項目可簡化元件組件的服務。 如果一或多個應用程式會使用具有組態檔位於已知位置中的組件，可以使用使用組件的應用程式的組態檔 **\<linkedConfiguration >** 包含組件的組態檔，而不是直接包括組態資訊的項目。 當元件組件受到服務時，更新常見的組態檔提供使用組件的所有應用程式的更新的組態資訊。

> [!NOTE]
>  **\<LinkedConfiguration >** 與 Windows 並排顯示的資訊清單的應用程式不支援項目。

下列規則管理連結的組態檔的使用：

- 包含的組態檔中設定只會影響載入器繫結原則，且僅供載入器。 包含的組態檔可能會有非繫結原則，設定，但這些設定不具有任何作用。

- 唯一支援的格式`href`屬性是`file://`。 支援本機檔案和 UNC 檔案。

- 連結的組態，每個組態檔的數目沒有限制。

- 所有連結的組態檔會合併以形成一個檔案，類似的行為`#include`C/c + + 指示詞。

-  **\<LinkedConfiguration >** 項目只允許在應用程式組態檔，它會忽略*Machine.config*。

- 已偵測到循環參考，並終止。 也就是說，如果 **\<linkedConfiguration >** 的一系列的組態檔項目形成迴圈，是偵測到迴圈，並將其停止。

## <a name="example"></a>範例

下列範例示範如何包含從本機硬碟的組態檔：

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [**\<Assemblybinding> >** 項目](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)
- [適用於.NET Framework 的組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
