---
title: 作法：建立列舉類型的新方法 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 2ca388d19c0e4e1b098076caa5baa0a83cc0dd4c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585870"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>作法：建立列舉類型的新方法 (C# 程式設計手冊)
您可以使用擴充方法來新增專屬於特定列舉類型的功能。  
  
## <a name="example"></a>範例  
 在下例中，`Grades` 列舉代表班上學生可能得到的字母分級成績。 已將名為 `Passing` 的擴充方法新增至 `Grades` 類型，以便該類型的每個執行個體現在都「知道」它是否代表傳遞等級。  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 請注意，`Extensions` 類別也包含動態更新的靜態變數，以及反映該變數目前值的擴充方法傳回值。 本例示範，在幕後直接對定義所在的靜態類別叫用擴充方法。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
