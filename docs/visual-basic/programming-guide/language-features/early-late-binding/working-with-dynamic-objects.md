---
title: "使用動態物件 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 366b563764baaa39849356a782ecee264b2ae94f
ms.lasthandoff: 03/13/2017

---
# <a name="working-with-dynamic-objects-visual-basic"></a>使用動態物件 (Visual Basic)
動態物件以外的其他提供另一種方式，`Object`類型，以在執行階段物件晚期繫結。 動態物件公開 （expose) 成員，例如屬性和方法在執行階段使用動態介面中定義的<xref:System.Dynamic>命名空間。</xref:System.Dynamic> 您可以使用中的類別<xref:System.Dynamic>命名空間來建立使用靜態型別或格式不相符的資料結構的物件。</xref:System.Dynamic> 您也可以使用諸如 IronPython 和 IronRuby 的動態語言中所定義的動態物件。 說明如何建立動態物件，或使用動態物件定義在動態語言的範例，請參閱[逐步解說︰ 建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)， <xref:System.Dynamic.DynamicObject>，或<xref:System.Dynamic.ExpandoObject>.</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]繫結至物件的動態語言執行階段和動態語言，例如 IronPython 和 IronRuby 使用<xref:System.Dynamic.IDynamicMetaObjectProvider>介面。</xref:System.Dynamic.IDynamicMetaObjectProvider> 實作的類別範例`IDynamicMetaObjectProvider`介面都是<xref:System.Dynamic.DynamicObject>和<xref:System.Dynamic.ExpandoObject>類別。</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject>  
  
 如果要實作的物件進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]繫結至動態的物件，使用該介面。 如果物件不會實作進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面，或如果呼叫`IDynamicMetaObjectProvider`介面失敗，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]繫結至物件，使用晚期繫結功能[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]執行階段。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Dynamic.DynamicObject></xref:System.Dynamic.DynamicObject>   
 <xref:System.Dynamic.ExpandoObject></xref:System.Dynamic.ExpandoObject>   
 [逐步解說︰ 建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)   
 [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
