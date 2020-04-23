---
title: XAML 中的 xml:space 處理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071434"
---
# <a name="xmlspace-handling-in-xaml"></a>XAML 中的 xml:space 處理

該`xml:space`屬性是一個 XML 定義的屬性,用於聲明物件元素中的重要空白處理行為。 此行為與聲明元素`xml:space`中包含的所有內容(內部文本)以及子元素的範圍相關。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object xml:space="preserve" />
```

 \- 或 -

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a>備註

XAML`xml:space`中屬性的定義包括其兩個可能的值,`xml:space`由 W3C XML 規範定義為"特殊屬性"。

屬性的`xml:space`預設值是文字`"default"`值 。 對於值`"default"`,或者`xml:space`如果 根本不指示,則重要的空白分析行為是預設處理,如[XAML 中的主題白空間處理中](white-space-processing.md)定義的默認處理。

要在物件元素內容中保留空白,請在`xml:space="preserve"`該物件元素上指定。

在大多數解釋下,`xml:space`屬性效果和屬性的值範圍限定為子元素。

有關 XAML 中空白處理的完整討論,請參閱[XAML 中的空白處理](white-space-processing.md)。

## <a name="see-also"></a>另請參閱

- [XAML 中的空白字元處理](white-space-processing.md)
- [XAML 概觀 (WPF)](../fundamentals/xaml.md)
