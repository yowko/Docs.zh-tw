---
title: HOW TO：使用字典儲存事件執行個體 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f3b8e313bd0b1bd3973102caebb9bbc9da620ae6
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203028"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>HOW TO：使用字典儲存事件執行個體 (C# 程式設計手冊)
`accessor-declarations` 的其中一個用途是公開許多事件，但不為每個事件配置欄位，而改為使用字典儲存事件執行個體。 這只有在您有許多事件，但預期不會實作大多數事件時才有用。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [事件](../../../csharp/programming-guide/events/index.md)
- [委派](../../../csharp/programming-guide/delegates/index.md)
