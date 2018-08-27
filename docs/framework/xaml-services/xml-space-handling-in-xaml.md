---
title: XAML 中的 xml:space 處理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 051cb6b3a314509e9593ee570fd659098670e88b
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925853"
---
# <a name="xmlspace-handling-in-xaml"></a>XAML 中的 xml:space 處理
`xml:space`屬性是宣告為物件項目內的顯著泛空白字元處理行為的 XML 定義的屬性。 此行為會與相關的項目內所包含的所有內容 （內部文字） 其中`xml:space`宣告，因此也會設定至子項目。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \-或-  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>備註  
 定義`xml:space`包括其兩個可能值的 XAML 中的屬性衍生自`xml:space`W3C XML 規格所定義為 「 特殊屬性 」。  
  
 預設值`xml:space`屬性是常值`"default"`。 值`"default"`，或者如果`xml:space`並未顯示，行為的顯著泛空白字元剖析為預設處理，主題中所定義[泛空白字元處理中 XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。  
  
 若要保留物件項目內容中的空白字元，請指定`xml:space="preserve"`該物件元素上。  
  
 在大部分的詮釋，`xml:space`屬性效果和屬性的值範圍都限於子項目。  
  
 泛空白字元處理在 XAML 中的完整討論，請參閱 <<c0> [ 泛空白字元處理中 XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 XAML 中處理泛空白字元](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
