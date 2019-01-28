---
title: HOW TO：使用字典儲存事件執行個體 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 8f0284c5637890f35642346880d035619bc0e1e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560057"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>HOW TO：使用字典儲存事件執行個體 (C# 程式設計手冊)
`accessor-declarations` 的其中一個用途是公開許多事件，但不為每個事件配置欄位，而改為使用字典儲存事件執行個體。 這只有在您有許多事件，但預期不會實作大多數事件時才有用。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [事件](../../../csharp/programming-guide/events/index.md)
- [委派](../../../csharp/programming-guide/delegates/index.md)
