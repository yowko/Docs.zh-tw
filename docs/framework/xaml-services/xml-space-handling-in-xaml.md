---
title: XAML 中的 xml:space 處理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: af971ad9ea74e123b939ff8d8488e4e45c5d4aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563463"
---
# <a name="xmlspace-handling-in-xaml"></a>XAML 中的 xml:space 處理
`xml:space`屬性是宣告的空白字元處理行為物件項目內的 XML 定義的屬性。 這個行為會與相關的項目內所包含的所有內容 （內部文字） 其中`xml:space`宣告，因此也會設定至子元素。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \-或-  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>備註  
 定義`xml:space`XAML 包括兩個可能的值中的屬性衍生自`xml:space`W3C XML 規格所定義為 「 特殊屬性 」。  
  
 預設值`xml:space`屬性是常值`"default"`。 值`"default"`，或如果`xml:space`並未顯示，空白字元剖析的行為是預設的處理，本主題中所定義[XAML 中的空白字元處理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。  
  
 若要保留物件元素內容內的空白字元，請指定`xml:space="preserve"`該物件項目。  
  
 在大部分的方式解讀`xml:space`屬性效果和屬性的值的範圍限於子項目。  
  
 如需 XAML 中處理空白字元的完整討論，請參閱[XAML 中的空白字元處理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XAML 中的泛空白字元處理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
