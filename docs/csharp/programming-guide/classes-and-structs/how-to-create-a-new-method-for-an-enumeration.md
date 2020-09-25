---
title: '如何建立列舉的新方法-c # 程式設計指南'
description: '瞭解如何使用擴充方法，以 c # 將功能加入至列舉。 這個範例會示範一個稱為「成績」之列舉傳遞的擴充方法。'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 2714b29d64e18250f0fe379aee1c09c242d3f63f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174260"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>如何建立列舉的新方法 (c # 程式設計手冊) 

您可以使用擴充方法來新增專屬於特定列舉類型的功能。  
  
## <a name="example"></a>範例  

 在下例中，`Grades` 列舉代表班上學生可能得到的字母分級成績。 已將名為 `Passing` 的擴充方法新增至 `Grades` 類型，以便該類型的每個執行個體現在都「知道」它是否代表傳遞等級。  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 請注意，`Extensions` 類別也包含動態更新的靜態變數，以及反映該變數目前值的擴充方法傳回值。 本例示範，在幕後直接對定義所在的靜態類別叫用擴充方法。  
  
## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [擴充方法](./extension-methods.md)
