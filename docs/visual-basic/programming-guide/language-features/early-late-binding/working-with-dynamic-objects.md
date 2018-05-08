---
title: 使用動態物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 78b17a379ea219cc24842322703caaa9d29eeb2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-dynamic-objects-visual-basic"></a>使用動態物件 (Visual Basic)
動態物件會提供另一種方法，除了`Object`類型，以在執行階段物件晚期繫結。 動態物件成員，例如屬性和方法在執行階段會使用公開中所定義的動態介面<xref:System.Dynamic>命名空間。 您可以使用中的類別<xref:System.Dynamic>命名空間，以建立使用的靜態類型或格式不相符的資料結構的物件。 您也可以使用動態語言，例如 IronPython 和 IronRuby 中所定義的動態物件。 如需示範如何建立動態物件，或使用動態語言所定義的動態物件的範例，請參閱[逐步解說： 建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)， <xref:System.Dynamic.DynamicObject>，或<xref:System.Dynamic.ExpandoObject>。  
  
 Visual Basic 中的繫結物件的動態語言執行階段和動態的語言，例如 IronPython 和 IronRuby 使用<xref:System.Dynamic.IDynamicMetaObjectProvider>介面。 類別實作的範例`IDynamicMetaObjectProvider`介面都是<xref:System.Dynamic.DynamicObject>和<xref:System.Dynamic.ExpandoObject>類別。  
  
 如果物件實作進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面、 Visual Basic 繫結到使用該介面的動態物件。 如果物件未實作進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面，或如果呼叫`IDynamicMetaObjectProvider`介面失敗時，使用 Visual Basic 執行階段的晚期繫結功能的 Visual Basic 繫結至物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
