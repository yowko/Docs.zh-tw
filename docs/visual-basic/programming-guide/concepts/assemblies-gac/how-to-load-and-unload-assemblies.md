---
title: 如何： 載入和卸載組件 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
ms.openlocfilehash: 1cec7a7e15843874b65cf5d2f3a23b8e644a26d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640566"
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>如何： 載入和卸載組件 (Visual Basic)
您的程式所參考的組件會在建置時自動載入，不過您也可以在執行階段，將特定組件載入目前的應用程式定義域。 如需詳細資訊，請參閱[如何：將組件載入應用程式定義域](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。  
  
 若要卸載個別組件，您必須先卸載所有包含該組件的應用程式定義域。 即使組件超出範圍，實際組件檔仍會保持載入狀態，直到卸載所有包含該組件的應用程式定義域為止。  
  
 如果您只想要卸載其中一部分組件，請考慮建立新的應用程式定義域、在該定義域內執行程式碼，然後卸載該應用程式定義域。 如需詳細資訊，請參閱[如何：卸載應用程式定義域](../../../../framework/app-domains/how-to-unload-an-application-domain.md)。  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>將組件載入應用程式定義域  
  
1.  使用 <xref:System.AppDomain> 和 <xref:System.Reflection> 類別中所含之數種載入方法的其中一種。 如需詳細資訊，請參閱[如何：將組件載入應用程式定義域](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。  
  
### <a name="to-unload-an-application-domain"></a>卸載應用程式定義域  
  
1.  若要卸載個別組件，您必須先卸載所有包含該組件的應用程式定義域。 使用 <xref:System.AppDomain> 中的 `Unload` 方法來卸載應用程式定義域。 如需詳細資訊，請參閱[如何：卸載應用程式定義域](../../../../framework/app-domains/how-to-unload-an-application-domain.md)。  
  
## <a name="see-also"></a>另請參閱  
 [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)  
 [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [如何：將組件載入應用程式定義域](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
