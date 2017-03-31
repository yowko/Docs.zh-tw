---
title: "如何：載入和卸載組件 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 15905b2c23320b57e5797d6084ce48cfc526ed7d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-load-and-unload-assemblies-c"></a>如何：載入和卸載組件 (C#)
您的程式所參考的組件會在建置時自動載入，不過您也可以在執行階段，將特定組件載入目前的應用程式定義域。 如需詳細資訊，請參閱[如何：將組件載入應用程式定義域](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)。  
  
 若要卸載個別組件，您必須先卸載所有包含該組件的應用程式定義域。 即使組件超出範圍，實際組件檔仍會保持載入狀態，直到卸載所有包含該組件的應用程式定義域為止。  
  
 如果您只想要卸載其中一部分組件，請考慮建立新的應用程式定義域、在該定義域內執行程式碼，然後卸載該應用程式定義域。 如需詳細資訊，請參閱[如何：卸載應用程式定義域](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)。  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>將組件載入應用程式定義域  
  
1.  使用 <xref:System.AppDomain> 和 <xref:System.Reflection> 類別所包含的其中一種載入方法。 如需詳細資訊，請參閱[如何：將組件載入應用程式定義域](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)。  
  
### <a name="to-unload-an-application-domain"></a>卸載應用程式定義域  
  
1.  若要卸載個別組件，您必須先卸載所有包含該組件的應用程式定義域。 使用 <xref:System.AppDomain> 中的 `Unload` 方法來卸載應用程式定義域。 如需詳細資訊，請參閱[如何：卸載應用程式定義域](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../../csharp/programming-guide/index.md)   
 [組件和全域組件快取 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)   
 [如何：將組件載入應用程式定義域](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)
