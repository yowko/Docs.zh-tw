---
title: <configuration> 的 <assemblyBinding> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921266"
---
# <a name="assemblybinding-element-for-configuration"></a>\<configuration > 的\<assemblyBinding > 元素

指定位於組態層級的組件繫結原則。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; **\<assemblyBinding>**

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

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-element"></a>子項目

|     | 描述 |
| --- | ----------- |
| [ **\<linkedConfiguration>** ](linkedconfiguration-element.md) | 指定要包含的組態檔。 |

## <a name="remarks"></a>備註

LinkedConfiguration > 元素藉由允許應用程式佈建檔在已知位置中包含元件設定檔, 而不是複製元件, 來簡化元件元件的管理。 [ **\<** ](linkedconfiguration-element.md)設定。

> [!NOTE]
> **
          \<LinkedConfiguration >** 與 Windows 並排顯示的資訊清單的應用程式不支援項目。

## <a name="example"></a>範例

下列範例顯示如何將設定檔包含在本機硬碟上:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
