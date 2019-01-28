---
title: HOW TO：定義抽象屬性 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: ab846f423631c8238ff9a516f95d32ff32bd0335
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616331"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>HOW TO：定義抽象屬性 (C# 程式設計手冊)
下例示範如何定義[抽象](../../../csharp/language-reference/keywords/abstract.md)屬性。 抽象屬性宣告不提供屬性存取子實作 -- 它會宣告類別支援屬性，但保留衍生類別的存取子實作。 下例示範如何實作繼承自基底類別的抽象屬性。  
  
 這個範例包含三個檔案，每個檔案都是各自編譯，產生的組件是下次編譯參考的對象：  
  
-   abstractshape.cs：包含抽象 `Area` 屬性的 `Shape` 類別。  
  
-   shapes.cs：`Shape` 類別的子類別。  
  
-   shapetest.cs：要顯示某些 `Shape` 衍生物件區域的測試程式。  
  
 若要編譯範例，請使用下列命令：  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 這會建立可執行檔 shapetest.exe。  
  
## <a name="example"></a>範例  
 這個檔案會宣告包含 `double` 類型 `Area` 屬性的 `Shape` 類別。  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   屬性的修飾詞是放在屬性宣告中。 例如：  
  
    ```csharp  
    public abstract double Area  
    ```  
  
-   宣告抽象屬性時 (例如本例的 `Area`)，您只要指出有哪些屬性存取子可用即可，不用實作它們。 本例中只有 [get](../../../csharp/language-reference/keywords/get.md) 存取子可用，所以此屬性是唯讀的。  
  
## <a name="example"></a>範例  
 下列程式碼會示範 `Shape` 的三個子類別，以及它們如何覆寫 `Area` 屬性以提供它們自己的實作。  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a>範例  
 下列程式碼會示範測試程式，建立多個 `Shape` 衍生物件並列印其區域。  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)
- [抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [如何：使用命令列建立和使用組件](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
