---
title: 使用動態物件
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 45f8b5c327d40f93b59c2115c75b3b7d385f5a8d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057919"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>使用動態物件 (Visual Basic)

動態物件提供的另一種方式是在 `Object` 執行時間晚期繫結至物件，而非類型。 動態物件會使用命名空間中定義的動態介面，在執行時間公開成員（例如屬性和方法） <xref:System.Dynamic> 。 您可以使用命名空間中的類別， <xref:System.Dynamic> 來建立使用不符合靜態類型或格式之資料結構的物件。 您也可以使用動態物件（例如 IronPython 和 IronRuby）中所定義的動態物件。 如需示範如何建立動態物件或使用動態語言所定義動態物件的範例，請參閱 [逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、 <xref:System.Dynamic.DynamicObject> 或 <xref:System.Dynamic.ExpandoObject> 。  
  
 Visual Basic 使用介面系結至動態語言執行時間中的物件和動態語言（例如 IronPython 和 IronRuby） <xref:System.Dynamic.IDynamicMetaObjectProvider> 。 執行介面之類別的範例 `IDynamicMetaObjectProvider` 為 <xref:System.Dynamic.DynamicObject> 和 <xref:System.Dynamic.ExpandoObject> 類別。  
  
 如果對執行介面的物件進行晚期繫結呼叫 `IDynamicMetaObjectProvider` ，Visual Basic 使用該介面系結至動態物件。 如果對未執行介面的物件進行晚期繫結呼叫 `IDynamicMetaObjectProvider` ，或對介面的呼叫 `IDynamicMetaObjectProvider` 失敗，Visual Basic 使用 Visual Basic 執行時間的晚期繫結功能來系結至物件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [早期和晚期繫結](index.md)
