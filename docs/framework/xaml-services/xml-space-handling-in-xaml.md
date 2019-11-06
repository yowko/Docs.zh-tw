---
title: XAML 中的 xml:space 處理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458800"
---
# <a name="xmlspace-handling-in-xaml"></a>XAML 中的 xml:space 處理
`xml:space` 屬性是 XML 定義的屬性，可宣告物件元素內的重要空白字元處理行為。 這個行為與在宣告 `xml:space` 的元素中包含的所有內容（內部文字）相關，也會將範圍設為子項目。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \-或-  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>備註  
 XAML 中 `xml:space` 屬性的定義，包括它的兩個可能值，衍生自 W3C 規格 for XML 定義為「特殊屬性」的 `xml:space`。  
  
 `xml:space` 屬性的預設值是 `"default"`的常值。 對於 `"default"`的值，或如果沒有指定 `xml:space`，則重大空白字元剖析的行為是預設處理，如[XAML 中的空白字元處理](whitespace-processing-in-xaml.md)主題中所定義。  
  
 若要保留物件專案內容中的空白字元，請在該物件元素上指定 `xml:space="preserve"`。  
  
 在大部分的解讀之下，`xml:space` 屬性效果和屬性的值都是以子項目為範圍。  
  
 如需 XAML 中空白字元處理的完整討論，請參閱[xaml 中](whitespace-processing-in-xaml.md)的空白字元處理。  
  
## <a name="see-also"></a>請參閱

- [XAML 中的空白字元處理](whitespace-processing-in-xaml.md)
- [XAML 概觀 (WPF)](../../desktop-wpf/fundamentals/xaml.md)
