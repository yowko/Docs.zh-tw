---
title: 使用動態物件
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 20d007fb48e1db352bab6d8e25d2e60e02554732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345168"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>使用動態物件 (Visual Basic)
動態物件提供另一種方式，而不是 `Object` 類型，以便在執行時間晚期繫結至物件。 動態物件會使用 <xref:System.Dynamic> 命名空間中定義的動態介面，在執行時間公開成員（例如屬性和方法）。 您可以使用 <xref:System.Dynamic> 命名空間中的類別來建立物件，以使用不符合靜態類型或格式的資料結構。 您也可以使用動態語言（例如 IronPython 和 IronRuby）中定義的動態物件。 如需示範如何建立動態物件或使用動態語言中所定義動態物件的範例，請參閱[逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、<xref:System.Dynamic.DynamicObject>或 <xref:System.Dynamic.ExpandoObject>。  
  
 Visual Basic 會使用 <xref:System.Dynamic.IDynamicMetaObjectProvider> 介面，從動態語言執行時間和動態語言（例如 IronPython 和 IronRuby）系結至物件。 執行 `IDynamicMetaObjectProvider` 介面的類別範例包括 <xref:System.Dynamic.DynamicObject> 和 <xref:System.Dynamic.ExpandoObject> 類別。  
  
 如果對執行 `IDynamicMetaObjectProvider` 介面的物件進行晚期繫結呼叫，Visual Basic 使用該介面系結至動態物件。 如果對未執行 `IDynamicMetaObjectProvider` 介面的物件進行晚期繫結呼叫，或呼叫 `IDynamicMetaObjectProvider` 介面失敗，Visual Basic 會使用 Visual Basic 執行時間的晚期繫結功能來系結至物件。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
