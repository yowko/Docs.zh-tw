---
title: 使用動態物件
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 13b7c80537700c934dbb807b0f264218357088ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405166"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>使用動態物件 (Visual Basic)
動態物件提供另一種方法，而不是 `Object` 類型，以便在執行時間晚期系結至物件。 動態物件會使用命名空間中定義的動態介面，在執行時間公開成員（例如屬性和方法） <xref:System.Dynamic> 。 您可以使用命名空間中的類別 <xref:System.Dynamic> 來建立物件，以使用不符合靜態類型或格式的資料結構。 您也可以使用動態語言（例如 IronPython 和 IronRuby）中定義的動態物件。 如需示範如何建立動態物件或使用動態語言中所定義動態物件的範例，請參閱[逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、 <xref:System.Dynamic.DynamicObject> 或 <xref:System.Dynamic.ExpandoObject> 。  
  
 Visual Basic 會使用介面，從動態語言執行時間和動態語言（例如 IronPython 和 IronRuby）系結至物件 <xref:System.Dynamic.IDynamicMetaObjectProvider> 。 執行介面的類別範例 `IDynamicMetaObjectProvider` 包括 <xref:System.Dynamic.DynamicObject> 和 <xref:System.Dynamic.ExpandoObject> 類別。  
  
 如果對執行介面的物件進行晚期繫結呼叫 `IDynamicMetaObjectProvider` ，Visual Basic 會使用該介面來系結至動態物件。 如果對未執行介面的物件進行晚期繫結呼叫 `IDynamicMetaObjectProvider` ，或介面的呼叫 `IDynamicMetaObjectProvider` 失敗，Visual Basic 會使用 Visual Basic 執行時間的晚期繫結功能來系結至物件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [早期和晚期繫結](index.md)
