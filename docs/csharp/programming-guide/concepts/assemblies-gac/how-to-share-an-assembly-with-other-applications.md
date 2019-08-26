---
title: 作法：與其他應用程式共用組件 (C#)
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 954db3fe139ff307386fc182dbf16c60ce86bd30
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595738"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>作法：與其他應用程式共用組件 (C#)
組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。  
  
 為了與其他應用程式共用組件，必須將該組件放在[全域組件快取](../../../../framework/app-domains/gac.md) (GAC) 中。  
  
### <a name="sharing-an-assembly"></a>共用組件  
  
1. 建立您的組件。 如需詳細資訊，請參閱[建立組件](../../../../framework/app-domains/create-assemblies.md)。  
  
2. 為您的組件指派強式名稱。 如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。  
  
3. 將版本資訊指派給您的組件。 如需詳細資訊，請參閱[組件版本控制](../../../../framework/app-domains/assembly-versioning.md)。  
  
4. 將您的組件新增至全域組件快取。 如需詳細資訊，請參閱[如何：在全域組件快取中安裝單一組件](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)。  
  
5. 從其他應用程式存取組件內含的類型。 如需詳細資訊，請參閱[如何：參考以強式名稱命名的組件](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../index.md)
- [使用組件設計程式](../../../../framework/app-domains/programming-with-assemblies.md)
