---
title: 作法：與其他應用程式共用組件
description: 請參閱如何在 .NET 中與其他應用程式共用元件。 元件可以是私用（預設值）或共用的。 若要共用元件，請將它放在 GAC 中。
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 9cef25059968875f17ce5dc77b04c44a2f3945f6
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104655"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>作法：與其他應用程式共用組件
組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。  

若要與其他應用程式共用元件，必須將它放在[全域組件快取（GAC）](gac.md)中。  
  
若要共用元件：
  
1. 建立您的組件。 如需詳細資訊，請參閱[建立元件](../../standard/assembly/create.md)。  
  
2. 為您的組件指派強式名稱。 如需詳細資訊，請參閱[如何：使用強式名稱簽署元件](../../standard/assembly/sign-strong-name.md)。  
  
3. 將版本資訊指派給您的組件。 如需詳細資訊，請參閱[元件版本控制](../../standard/assembly/versioning.md)。  
  
4. 將您的元件加入至全域組件快取。 如需詳細資訊，請參閱[如何：將元件安裝到全域組件快取](install-assembly-into-gac.md)中。  
  
5. 從其他應用程式存取元件中包含的類型。 如需詳細資訊，請參閱[如何：參考強式名稱的元件](../../standard/assembly/reference-strong-named.md)。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../../../api/index.md)
- [程式設計概念（Visual Basic）](../../../api/index.md)
- [具有組件的程式](../../standard/assembly/index.md)
