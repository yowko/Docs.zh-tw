---
title: HOW TO：共用組件與其他應用程式 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: 520fe69d30ca55251ae7a19dcd7a1ea0c11e7bd5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302214"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a>HOW TO：共用組件與其他應用程式 (Visual Basic)
組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。  
  
 為了與其他應用程式共用組件，必須將該組件放在[全域組件快取](../../../../framework/app-domains/gac.md) (GAC) 中。  
  
### <a name="sharing-an-assembly"></a>共用組件  
  
1. 建立您的組件。 如需詳細資訊，請參閱[建立組件](../../../../framework/app-domains/create-assemblies.md)。  
  
2. 為您的組件指派強式名稱。 如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。  
  
3. 將版本資訊指派給您的組件。 如需詳細資訊，請參閱[組件版本控制](../../../../framework/app-domains/assembly-versioning.md)。  
  
4. 將您的組件新增至全域組件快取。 如需詳細資訊，請參閱[如何：在全域組件快取中安裝單一組件](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)。  
  
5. 從其他應用程式存取組件內含的類型。 如需詳細資訊，請參閱[如何：參考以強式名稱命名的組件](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)。  
  
## <a name="see-also"></a>另請參閱

- [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)
- [.NET 中的組件](../../../../standard/assembly/index.md)
- [使用組件設計程式](../../../../framework/app-domains/programming-with-assemblies.md)
