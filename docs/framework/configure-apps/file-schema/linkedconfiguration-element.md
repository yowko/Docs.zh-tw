---
title: <linkedConfiguration> 項目
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
ms.openlocfilehash: a0b56ac66302f11c59c149197a84bb96691282a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921006"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration > 元素

指定要包含的組態檔。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<assemblyBinding>** ](assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration>**

## <a name="syntax"></a>語法

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **href**  | 必要屬性。<br><br>要包含的設定檔的 URL。 **Href**屬性唯一支援的格式為`file://`。 支援本機檔案和 UNC 檔案。 |

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [ **assemblyBinding>\<** 元素](assemblybinding-element-for-configuration.md) | 指定位於組態層級的組件繫結原則。 |

## <a name="child-elements"></a>子元素

無

## <a name="remarks"></a>備註

LinkedConfiguration > 元素會簡化元件元件的服務。 **\<** 如果一或多個應用程式使用的元件具有位於已知位置的設定檔, 則使用該元件之應用程式的設定檔案可以使用 **\<linkedConfiguration >** 元素來包含元件設定檔, 而不是直接包含設定資訊。 服務元件元件時, 更新通用設定檔案會將更新的設定資訊提供給所有使用該元件的應用程式。

> [!NOTE]
> **
          \<LinkedConfiguration >** 與 Windows 並排顯示的資訊清單的應用程式不支援項目。

下列規則會管理連結的設定檔使用:

- 包含的設定檔案中的設定只會影響載入器系結原則, 而且僅供載入器使用。 包含的設定檔案可以具有系結原則以外的設定, 但這些設定不會有任何作用。

- `href`屬性唯一支援的格式為`file://`。 支援本機檔案和 UNC 檔案。

- 每個設定檔的連結設定數目沒有條件約束。

- 所有連結的設定檔都會合並成一個檔案, 類似于 C/ `#include` C++中指示詞的行為。

- 只有在應用程式佈建檔中,  **\<才允許 linkedConfiguration >** 元素; machine.config 中會忽略它。

- 偵測到迴圈參考並結束。 也就是說, 如果 **\<linkedConfiguration >** 一系列設定檔中的元素形成迴圈, 就會偵測到迴圈並停止。

## <a name="example"></a>範例

下列範例顯示如何包含本機硬碟的設定檔:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [ **assemblyBinding>\<** 元素](assemblybinding-element-for-configuration.md)
- [.NET Framework 的設定檔架構](index.md)
