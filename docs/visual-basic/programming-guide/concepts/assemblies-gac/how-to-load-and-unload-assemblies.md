---
title: "如何︰ 載入和卸載組件 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 460d3a18fdee74c9b9c49ee465247b5b12d554d8
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>如何︰ 載入和卸載組件 (Visual Basic)
您的程式所參考的組件會自動載入在建置階段，但是也可以在特定的組件載入目前應用程式定義域在執行階段。 如需詳細資訊，請參閱[How to︰ 載入組件的應用程式定義域](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)。  
  
 沒有任何方法，而不需卸載所有包含它之應用程式定義域卸載個別組件。 即使組件超出範圍時，實際的組件檔會保持載入，直到包含它的所有應用程式定義域，就會卸載。  
  
 如果您想要卸載某些組件而非其他電腦，請考慮建立新的應用程式定義域執行該網域內的程式碼，然後卸載該應用程式定義域。 如需詳細資訊，請參閱[如何︰ 卸載應用程式定義域](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)。  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>應用程式定義域載入組件  
  
1.  使用其中一種類別<xref:System.AppDomain>和<xref:System.Reflection>.</xref:System.Reflection></xref:System.AppDomain>中所包含的載入方法 如需詳細資訊，請參閱[How to︰ 載入組件的應用程式定義域](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)。  
  
### <a name="to-unload-an-application-domain"></a>卸載應用程式定義域  
  
1.  沒有任何方法，而不需卸載所有包含它之應用程式定義域卸載個別組件。 使用`Unload`方法從<xref:System.AppDomain>卸載應用程式定義域。</xref:System.AppDomain> 如需詳細資訊，請參閱[如何︰ 卸載應用程式定義域](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)。  
  
## <a name="see-also"></a>另請參閱  
 [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)   
 [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [如何︰ 將應用程式定義域載入組件](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)
