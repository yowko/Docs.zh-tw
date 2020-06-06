---
title: <appSettings> 的 <remove> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215480"
---
# <a name="remove-element-for-appsettings"></a>\<appSettings> 的 \<remove> 項目

移除自訂應用程式設定。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>語法

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>屬性

|         | 描述 |
| ------- | ----------- |
| **key** | 必要屬性。<br><br>指定要移除之索引鍵的名稱。 |

### <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | 包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。 |

## <a name="child-elements"></a>子元素

None

## <a name="example"></a>範例

下列範例顯示如何移除的自訂設定 `ApplicationName` ：

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](../index.md)
