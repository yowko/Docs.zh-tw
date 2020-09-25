---
title: '如何將委派結合 (多播委派) -c # 程式設計指南'
description: 瞭解如何結合委派以建立多播委派。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 3e86c8ed4b7b091ee8c75930d427c22aa5bc0c52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185947"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a>如何合併委派 (多點傳送委派) (C# 程式設計手冊)

本例示範如何建立多點傳送委派。 [delegate](../../language-reference/builtin-types/reference-types.md) 物件有一個有用的屬性，是可以使用 `+` 運算子將多個物件指派給一個委派執行個體。 多點傳送委派包含指派委派的清單。 呼叫多點傳送委派時，會依序叫用清單中的委派。 只有相同類型的委派可以合併。  
  
 您可使用 `-` 運算子從多點傳送委派移除元件委派。  
  
## <a name="example"></a>範例  

 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.MulticastDelegate>
- [C # 程式設計指南](../index.md)
- [事件](../events/index.md)
