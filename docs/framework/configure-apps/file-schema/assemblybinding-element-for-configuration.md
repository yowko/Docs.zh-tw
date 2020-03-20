---
title: <configuration> 的 <assemblyBinding> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155475"
---
# <a name="assemblybinding-element-for-configuration"></a>\<用於\<配置>的程式集綁定>元素

指定位於組態層級的組件繫結原則。

&nbsp; [** \<配置>**](configuration-element.md)&nbsp;**程式集綁定>\<**

## <a name="syntax"></a>語法

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **xmlns** | 必要屬性。<br><br>指定組件繫結所需的 XML 命名空間。 使用字串 "urn:schemas-microsoft-com:asm.v1" 做為值。 |

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<配置>**](configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-element"></a>子項目

|     | 描述 |
| --- | ----------- |
| [**\<連結配置>**](linkedconfiguration-element.md) | 指定要包含的組態檔。 |

## <a name="remarks"></a>備註

[** \<連結配置>**](linkedconfiguration-element.md)元素允許應用程式佈建檔在已知位置包含程式集設定檔，而不是複製程式集配置設置，從而簡化了元件程式集的管理。

> [!NOTE]
> 對於具有 Windows 並行清單的應用程式，不支援**\<連結的配置>** 元素。

## <a name="example"></a>範例

下面的示例演示如何在本地硬碟上包含設定檔：

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [.NET 框架的設定檔架構](index.md)
