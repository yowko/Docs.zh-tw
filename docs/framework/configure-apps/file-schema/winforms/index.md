---
title: Windows Form 組態區段
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4a54df0b6301f1aae14d5561c91c6792cb0a1620
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109817"
---
# <a name="windows-forms-configuration-section"></a>Windows Form 組態區段
Windows Forms 組態設定允許 Windows Forms 應用程式儲存並擷取有關自訂應用程式設定 (例如多重監視器支援、高 DPI 支援，以及其他預先定義的組態設定) 的資訊。

Windows Forms 應用程式組態設定是儲存在應用程式組態檔的 `System.Windows.Forms.ApplicationConfigurationSection` 元素中。

## <a name="syntax"></a>語法

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a>屬性和元素

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

項目  |描述 |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | 新增具有指定值的組態設定金鑰 |

### <a name="parent-elements"></a>父元素

項目  |描述 |
---------|---------|
[\<configuration>](../configuration-element.md) | 通用語言執行平台和 Windows Forms 應用程式所使用之每個組態檔中的根元素 |

## <a name="remarks"></a>備註

從 .NET Framework 4.7 開始，`<System.Windows.Forms.ApplicationConfigurationSection>` 元素能允許您設定 Windows Forms 應用程式，以利用 .NET Framework 最新版本中的新增功能。 

`<System.Windows.Forms.ApplicationConfigurationSection>` 元素可以包含一或多個子 [`<add>`](windows-forms-add-configuration-element.md) 元素，每個子元素都能定義一個特定的組態設定。

## <a name="see-also"></a>請參閱

- [組態檔結構描述](../index.md)
- [Windows Forms 中的高 DPI 支援](../../../winforms/high-dpi-support-in-windows-forms.md)
