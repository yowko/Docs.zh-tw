---
title: static (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: b7e2981c8832d6ac1744c102d5bde55bbe25c256
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959981"
---
# <a name="static-c-reference"></a>static (C# 參考)
使用 `static` 修飾詞來宣告靜態成員，而靜態成員屬於類型本身，而不是特定物件。 `static` 修飾詞可以與類別、欄位、方法、屬性、運算子、事件和建構函式搭配使用，但不能與索引子、完成項或類別以外的類型搭配使用。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
## <a name="example"></a>範例  
 下列類別宣告為 `static`，並且只包含 `static` 方法：  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 常數或型別宣告隱含為靜態成員。  
  
 靜態成員無法透過執行個體進行參考。 而是透過類型名稱進行參考。 例如，請參考下列類別：  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 若要參照靜態成員 `x`，除非可以從相同的範圍存取該成員，否則請使用完整名稱 `MyBaseC.MyStruct.x`︰  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 雖然類別的執行個體包含類別的所有執行個體欄位的個別複本，但是每個靜態欄位都只會有一個複本。  
  
 無法使用 [this](../../../csharp/language-reference/keywords/this.md) 來參考靜態方法或屬性存取子。  
  
 如果將 `static` 關鍵字套用至類別，則類別的所有成員都必須是靜態。  
  
 類別和靜態類別可能會有靜態建構函式。 在啟動程式時與具現化類別時之間的某個點，會呼叫靜態建構函式。  
  
> [!NOTE]
>  `static` 關鍵字的使用方式比在 C++ 中受到更多限制。 若要與 C++ 關鍵字進行比較，請參閱[儲存類別 (C++)](/cpp/cpp/storage-classes-cpp#static)。
  
 若要示範靜態成員，請考慮使用代表公司員工的類別。 假設此類別包含可計算員工人數的方法以及可儲存員工人數的欄位。 方法和欄位都不屬於任何執行個體員工。 相反地，它們屬於公司類別。 因此，它們應該宣告為類別的靜態成員。  
  
## <a name="example"></a>範例  
 這個範例會讀取新員工的名稱和識別碼，並將員工計數器遞加一，然後顯示新員工和新員工人數的資訊。 為求簡單，此程式會從鍵盤讀取目前的員工人數。 在實際的應用程式中，應該從檔案讀取這項資訊。  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a>範例  
 這個範例示範，雖然您可以使用另一個尚未宣告的靜態欄位來初始化靜態欄位，但是除非將值明確指派給靜態欄位，否則不會定義結果。  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)  
 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
