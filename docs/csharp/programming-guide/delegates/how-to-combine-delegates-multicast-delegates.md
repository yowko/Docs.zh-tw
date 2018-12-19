---
title: HOW TO：組合委派 (多點傳送委派) - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d835f9b22fef550d6e73cbd620a283bd71e393ec
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237788"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>HOW TO：組合委派 (多點傳送委派) (C# 程式設計指南)
本例示範如何建立多點傳送委派。 [delegate](../../../csharp/language-reference/keywords/delegate.md) 物件有一個有用的屬性，是可以使用 `+` 運算子將多個物件指派給一個委派執行個體。 多點傳送委派包含指派委派的清單。 呼叫多點傳送委派時，會依序叫用清單中的委派。 只有相同類型的委派可以合併。  
  
 您可使用 `-` 運算子從多點傳送委派移除元件委派。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.MulticastDelegate>  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [事件](../../../csharp/programming-guide/events/index.md)
