---
title: 使用動態物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: ea7d7aae1cd79a0243a9c721b5e3958fba82f84f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832069"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>使用動態物件 (Visual Basic)
動態物件會提供另一種方式，而非`Object`類型，以在執行階段在物件的晚期繫結。 動態物件在執行階段公開成員，例如屬性和方法，藉由使用動態中所定義的介面<xref:System.Dynamic>命名空間。 您可以使用中的類別<xref:System.Dynamic>命名空間，以建立靜態類型或格式不相符的資料結構所使用的物件。 您也可以使用 IronPython 和 IronRuby 之類的動態語言中所定義的動態物件。 如需示範如何建立動態物件，或使用動態語言所定義的動態物件的範例，請參閱[逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)， <xref:System.Dynamic.DynamicObject>，或<xref:System.Dynamic.ExpandoObject>。  
  
 Visual Basic 中的繫結物件的動態語言執行平台和動態語言 IronPython 和 IronRuby 之類使用<xref:System.Dynamic.IDynamicMetaObjectProvider>介面。 範例類別可實作`IDynamicMetaObjectProvider`介面會<xref:System.Dynamic.DynamicObject>和<xref:System.Dynamic.ExpandoObject>類別。  
  
 如果晚期繫結進行呼叫，以實作的物件`IDynamicMetaObjectProvider`介面，以使用該介面的動態物件的 Visual Basic 繫結。 如果晚期繫結呼叫對物件未實作`IDynamicMetaObjectProvider`介面，或如果呼叫`IDynamicMetaObjectProvider`介面失敗時，Visual Basic 繫結至物件所使用的 Visual Basic 執行階段的晚期繫結功能。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
