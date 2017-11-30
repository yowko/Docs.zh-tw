---
title: "使用動態物件 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da70c1e4c7398ad46d48c85b62ab884675bd1a73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-dynamic-objects-visual-basic"></a>使用動態物件 (Visual Basic)
動態物件會提供另一種方法，除了`Object`類型，以在執行階段物件晚期繫結。 動態物件成員，例如屬性和方法在執行階段會使用公開中所定義的動態介面<xref:System.Dynamic>命名空間。 您可以使用中的類別<xref:System.Dynamic>命名空間，以建立使用的靜態類型或格式不相符的資料結構的物件。 您也可以使用動態語言，例如 IronPython 和 IronRuby 中所定義的動態物件。 如需示範如何建立動態物件，或使用動態語言所定義的動態物件的範例，請參閱[逐步解說： 建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)， <xref:System.Dynamic.DynamicObject>，或<xref:System.Dynamic.ExpandoObject>。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]將其使用的繫結至物件從動態語言執行階段及動態的語言，例如 IronPython 和 IronRuby<xref:System.Dynamic.IDynamicMetaObjectProvider>介面。 類別實作的範例`IDynamicMetaObjectProvider`介面都是<xref:System.Dynamic.DynamicObject>和<xref:System.Dynamic.ExpandoObject>類別。  
  
 如果物件實作進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]使用該介面的繫結的動態物件。 如果物件未實作進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面，或如果呼叫`IDynamicMetaObjectProvider`介面失敗，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]使用晚期繫結功能的繫結至物件[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]執行階段。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
