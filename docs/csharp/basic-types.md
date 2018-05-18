---
title: 基本類型 - C# 手冊
description: 了解所有 C# 程式中的核心類型 (數字、字串和物件)
ms.date: 10/10/2016
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 2e62a461e41f4172bd6dd512a71babb998924978
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="types-variables-and-values"></a>類型、變數和值  
C# 是強型別語言。 每個變數和常數都有型別，如同每個會評估為值的運算式一般。 每種方法簽章都會指定每個輸入參數與其傳回值的型別。 .NET Framework Class Library 會定義一組內建數字型別以及較複雜型別，代表各種邏輯建構，例如檔案系統、網路連線、物件集合與陣列，以及日期。 一般 C# 程式會使用類別庫的型別和使用者定義的型別，模型化程式的問題領域特有概念。  
  
可儲存在型別中的資訊包括下列各項：  
  
-   型別的變數需要的儲存空間。  
  
-   它可以代表的最大值和最小值。  
  
-   它所包含的成員 (方法、欄位、事件等等)。  
  
-   它繼承自的基底型別。  
  
-   將在執行階段配置給變數的記憶體位置。  
  
-   允許的作業類型。  
  
編譯器會使用型別資訊，來確認在您的程式碼中執行的全部都是「型別安全」的作業。 例如，如果您宣告型別 [int](language-reference/keywords/int.md) 的變數，編譯器會允許您使用額外的變數和減法運算。 如果您嘗試針對型別 [bool](language-reference/keywords/bool.md) 的變數執行相同作業，編譯器會產生錯誤，如下列範例所示︰  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
>  C 和 C++ 開發人員要注意在 C# 中，[bool](language-reference/keywords/bool.md) 不能轉換為 [int](language-reference/keywords/int.md)。  
  
編譯器會將型別資訊視為中繼資料內嵌至可執行檔。 Common Language Runtime (CLR) 會在執行階段使用該中繼資料，以在它配置和回收記憶體時進一步保證型別安全。  

## <a name="specifying-types-in-variable-declarations"></a>在變數宣告中指定類型  
當您在程式中宣告變數或常數時，必須指定其類型，或使用 [var](language-reference/keywords/var.md) 關鍵字以讓編譯器推斷其類型。 下列範例示範一些變數宣告，使用內建的數字型別和複雜的使用者定義型別︰  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
在方法簽章中指定方法參數和傳回值的型別。 下列簽章顯示的方法要求 [int](language-reference/keywords/int.md) 做為輸入引數且會傳回字串︰  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
宣告變數之後，不能以新型別重新宣告它，也無法將與所宣告型別不相容的值指派給它。 例如，您無法宣告 [int](language-reference/keywords/int.md) 並將為 [true](language-reference/keywords/true.md) 的布林值指派給它。 不過，可以將值轉換為其他型別，例如，指派給新的變數，或做為方法引數傳遞時。 編譯器會自動執行不會造成資料遺失的「型別轉換」作業。 而可能導致資料遺失的轉換在原始程式碼中需要有「轉換」。 

如需詳細資訊，請參閱[轉換和類型轉換](programming-guide/types/casting-and-type-conversions.md)。
 
## <a name="built-in-types"></a>內建類型
C# 提供一組標準內建數字類型，代表整數、浮點數值、布林運算式、文字字元、十進位值及其他資料型別。 另外還有內建的 **string** 和 **object** 類型。 這些都可供您在任何 C# 程式中使用。 如需內建型別的詳細資訊，請參閱[型別的參考表](language-reference/keywords/reference-tables-for-types.md)。  
  
## <a name="custom-types"></a>自訂類型  
您可以使用 [struct](language-reference/keywords/class.md)、[class](language-reference/keywords/class.md)、[interface](language-reference/keywords/interface.md) 和 [enum](language-reference/keywords/enum.md) 建構來建立您自己的自訂類型。 .NET Framework Class Library 本身是 Microsoft 所提供的自訂型別集合，您可以在自己的應用程式中使用。 根據預設，類別庫中最常使用的型別可用於任何 C# 程式中。 只有當您明確地將專案參考新增至定義所在的組件時，才能使用其他類型。 編譯器在有該組件的參考之後，您可以針對在原始程式碼的那個組件中宣告的型別宣告變數 (和常數) 。 
  
## <a name="generic-types"></a>泛型類型  
您可以使用一或多個「型別參數」來宣告類型，作為預留位置 (具象類型)，以供用戶端程式碼在其建立該類型的執行個體時提供實際類型。 這類的類型稱為「泛型型別」。 例如，.NET Framework 型別 <xref:System.Collections.Generic.List%601> 有一個型別參數，依慣例命名為 *T*。當您建立該型別的執行個體時，您會指定該清單將包含的物件型別，例如 string：  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)] 
  
使用型別參數讓您能夠重複使用相同的類別來保存任何元素型別，而不需要將每個元素都轉換成 [object](language-reference/keywords/object.md)。 泛型集合類別則稱為「強型別集合」，因為編譯器知道集合元素的特定型別，如果您嘗試將整數加入至上一個範例中的 `strings` 物件，便會在編譯時期引發錯誤。 如需詳細資訊，請參閱[泛型](programming-guide/generics/index.md)。 

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>隱含類型、匿名型別和 Tuple 類型  
如先前所述，您可以使用 [var](language-reference/keywords/var.md) 關鍵字，隱含地輸入區域變數 (但不是類別成員)。 變數還是會在編譯時期收到類型，但其是由編譯器所提供的類型。 如需詳細資訊，請參閱[隱含類型區域變數](programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
在某些情況下，不方便為一組您不想要儲存或在方法界限外傳遞的簡單相關值，建立簡單的具名類型。 為此，您可以建立「匿名型別」。 如需詳細資訊，請參閱[匿名型別](programming-guide/classes-and-structs/anonymous-types.md)。

通常會想要從方法傳回多個值。 您可以建立在單一方法呼叫中傳回多個值的「Tuple 類型」。 如需詳細資訊，請參閱 [Tuple](tuples.md)。

## <a name="the-common-type-system"></a>一般型別系統  
請務必了解 .NET Framework 中有關型別系統的兩個基本概念：  
  
-   它支援繼承準則。 型別可以衍生自稱為「基底型別」的其他型別。 衍生的型別會繼承 (有部份限制) 基底型別的方法、屬性和其他成員。 基底類型同樣可以衍生自一些其他類型，衍生類型則會繼承其繼承階層架構中兩個基底類型的成員。 所有類型 (包括 <xref:System.Int32> 這類內建數字類型 (C# 關鍵字：`int`)) 最終衍生自單一基底類型，即 <xref:System.Object> (C# 關鍵字：`object`)。 這種統一類型階層架構稱為[一般型別系統](../standard/common-type-system.md) (CTS)。 如需 C# 中有關繼承的詳細資訊，請參閱[繼承](programming-guide/classes-and-structs/inheritance.md)。  
  
-   CTS 中的每個型別都會定義為「實值型別」或「參考型別」。 這包括 .NET Framework Class Library 中的所有自訂類型以及您自己的使用者定義型別。 您使用 [struct](language-reference/keywords/struct.md) 關鍵字定義的類型為實值型別；所有內建數字類型都是 **struct**。 如需實值型別的詳細資訊，請參閱[結構](structs.md)。 您使用 [class](language-reference/keywords/class.md) 關鍵字定義的類型為參考型別。 如需參考型別的詳細資訊，請參閱[類別](classes.md)。 參考型別和實值型別有不同的編譯時期規則和不同的執行階段行為。
 
  
## <a name="see-also"></a>另請參閱
[結構](structs.md)
[類別](classes.md)
