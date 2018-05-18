---
title: 如何：使用字典儲存事件執行個體 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 97a7b0f168e4a1c81ec396f42b731dabb45b3516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>如何：使用字典儲存事件執行個體 (C# 程式設計手冊)
`accessor-declarations` 的其中一個用途是公開許多事件，但不為每個事件配置欄位，而改為使用字典儲存事件執行個體。 這只有在您有許多事件，但預期不會實作大多數事件時才有用。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [事件](../../../csharp/programming-guide/events/index.md)  
 [委派](../../../csharp/programming-guide/delegates/index.md)
