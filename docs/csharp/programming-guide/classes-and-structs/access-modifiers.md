---
title: 存取修飾詞 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 4be248b1d86692bd35491e55b1c649cd8428a33b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43406351"
---
# <a name="access-modifiers-c-programming-guide"></a>存取修飾詞 (C# 程式設計手冊)
所有類型和類型成員都具有存取範圍層級，以控制是否可以從組件中的其他程式碼或其他組件中使用它們。 您可以使用下列存取修飾詞，以在宣告類型或成員時指定其存取範圍：  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 類型或成員可由相同組件或參考該組件的另一個組件中的任何其他程式碼存取。 
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 類型或成員只能由相同類別或結構中的程式碼進行存取。  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 類型或成員只可由相同類別或衍生自該類別之類別中的程式碼進行存取。  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 類型或成員可由相同組件中的任何程式碼存取，但是不包括其他組件中的程式碼。  
  
 [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) 類型或成員可由宣告程式碼的組件內之任一程式碼存取，或是從另一個組件中的衍生類別內存取。 

 [private protected](../../../csharp/language-reference/keywords/private-protected.md) 類型或成員只可從其宣告組件內存取，或是從衍生自該類別之相同類別或類型的程式碼存取。
  
 下列範例示範如何指定類型和成員的存取修飾詞︰  
  
 [!code-csharp[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]  
  
 並非所有存取修飾詞都可以供所有類型或成員在所有內容中使用；而且，在某些情況下，類型成員的存取範圍會受限於其包含類型的存取範圍。 下列各節提供存取範圍的詳細資料。  
  
## <a name="class-and-struct-accessibility"></a>類別和結構存取範圍  
 直接在命名空間內宣告的類別和結構 (換句話說，未巢狀在其他類別或結構內) 可以是 public 或 internal。 如果未指定任何存取修飾詞，則 internal 是預設值。  
  
 結構成員 (包括巢狀類別和結構) 可以宣告為 public、internal 或 private。 類別成員，包含巢狀類別和結構，可為 public、protected internal、protected、internal、private protected 或 private。 類別成員和結構成員 (包括巢狀類別和結構) 的存取層級預設為 private。 無法從包含類型外部存取私用巢狀型別。  
  
 衍生類別的存取範圍不能大於其基底類型。 換句話說，您不能有衍生自內部類別 `A` 的公用類別 `B`。 因為 `A` 的所有 protected 或 internal 成員都可以從衍生類別進行存取，所以如果允許這樣做，則會有將 `A` 設為 public 的效果。  
  
 您可以使用 InternalsVisibleToAttribute 來啟用特定其他組件存取您的內部類型。 如需詳細資訊，請參閱 [Friend Assemblies](../concepts/assemblies-gac/friend-assemblies.md) (Friend 組件)。  
  
## <a name="class-and-struct-member-accessibility"></a>類別和結構成員存取範圍  
 您可使用六種存取類型的任一種，宣告類別成員 (包括巢狀類別和結構)。 因為結構不支援繼承，所以無法將結構成員宣告為 protected。  
  
 一般而言，成員存取範圍不會大於包含它之類型的存取範圍。 不過，如果成員實作介面方法，或覆寫公用基底類別中所定義的虛擬方法，則可以從組件外部存取內部類別的公用成員。  
  
 為欄位、屬性或事件之任何成員的類型必須至少與成員本身一樣可進行存取。 同樣地，傳回型別以及本身為方法、索引子或委派之任何成員的參數類型都必須至少像該成員本身一樣可供存取。 例如，除非 `C` 也是公用的，否則您無法有傳回 `C` 類別的公用方法 `M`。 同樣地，如果將 `A` 宣告為 private，則您不能有 `A` 類型的 protected 屬性。  
  
 使用者定義的運算子一律必須宣告為 public。 如需詳細資訊，請參閱 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)。  
  
 完成項不能有存取範圍修飾詞。  
  
 若要設定類別或結構成員的存取層級，請在成員宣告中新增適當的關鍵字，如下列範例所示。  
  
 [!code-csharp[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  protected internal 存取範圍層級表示「protected 或 internal」，而非「protected 和 internal」。 換句話說，可以從相同組件的任何類別 (包括衍生類別) 中存取 protected internal 成員。 若要僅限於相同組件中衍生類別的存取範圍，請將類別本身宣告為 internal，並將它的成員宣告為 protected。 此外，從 C# 7.2 開始，您可使用 private protected 存取修飾詞來達到相同的結果，而無須將包含的類別設為 internal。  
  
## <a name="other-types"></a>其他類型  
 直接在命名空間內宣告的介面可以宣告為 public 或 internal；而且，就像類別和結構，介面預設為內部存取。 介面成員一律都是 public，因為介面的目的是要讓其他類型存取類別或結構。 沒有存取修飾詞可以套用至介面成員。  
  
 列舉成員一律為 public，因此無法套用任何存取修飾詞。  
  
 委派的行為類似類別和結構。 根據預設，它們在直接在命名空間內宣告時會具有 internal 存取，而且在巢狀時會具有 private 存取。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [介面](../../../csharp/programming-guide/interfaces/index.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [protected internal](../../../csharp/language-reference/keywords/protected-internal.md)  
 [private protected](../../../csharp/language-reference/keywords/private-protected.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [interface](../../../csharp/language-reference/keywords/interface.md)
