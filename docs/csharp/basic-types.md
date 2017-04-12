---
title: "基本類型 | C# 手冊"
description: "了解所有 C# 程式中的核心類型 (數字、字串和物件)"
keywords: .NET, .NET Core, C#
author: BillWagner
ms.author: wiwagn
ms.date: 10/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 57c5524a18535778db337500b0a7e9013ce93519
ms.lasthandoff: 03/13/2017

---

# <a name="types-variables-and-values"></a>類型、變數和值  
C# 是強型別語言。 每個變數和常數都有類型，如同每個會評估為值的運算式一樣。 每個方法簽章都會指定每個輸入參數與其傳回值的類型。 .NET Framework Class Library 會定義一組內建數字類型以及代表各種邏輯建構的較複雜類型，例如檔案系統、網路連線、集合與陣列，以及日期。 一般 C# 程式會使用類別庫的類型和使用者定義型別，來模型化程式的問題領域特有概念。  
  
可儲存在類型中的資訊包括下列各項：  
  
-   類型的變數所需要的儲存空間。  
  
-   它可以代表的最大值和最小值。  
  
-   它所包含的成員 (方法、欄位、事件等等)。  
  
-   它所繼承的來源基底類型。  
  
-   將在執行階段配置給變數的記憶體位置。  
  
-   允許的作業類型。  
  
編譯器會使用類型資訊，來確認在您的程式碼中執行的全部都是「型別安全」**的作業。 例如，如果您宣告 [int](https://msdn.microsoft.com/library/5kzh1b5w.aspx) 類型的變數，則編譯器會允許您在加法和減法運算中使用這個變數。 如果您嘗試針對 [bool](https://msdn.microsoft.com/library/c8f5xwh7.aspx) 類型的變數執行相同作業，則編譯器會產生錯誤，如下列範例所示︰  
  
[!code-csharp[型別安全](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
>  C 和 C++ 開發人員要注意在 C# 中，[bool](https://msdn.microsoft.com/library/c8f5xwh7.aspx) 不能轉換為 [int](https://msdn.microsoft.com/library/5kzh1b5w.aspx)。  
  
編譯器會將類型資訊視為中繼資料內嵌至可執行檔。 Common Language Runtime (CLR) 會在執行階段使用該中繼資料，以在它配置和回收記憶體時進一步保證型別安全。  

## <a name="specifying-types-in-variable-declarations"></a>在變數宣告中指定類型  
當您在程式中宣告變數或常數時，必須指定其類型，或使用 [var](https://msdn.microsoft.com/library/bb383973.aspx) 關鍵字以讓編譯器推斷其類型。 下列範例示範一些使用內建數字類型和複雜使用者定義型別的變數宣告︰  
  
[!code-csharp[變數宣告](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
在方法簽章中指定方法參數和傳回值的類型。 下列簽章顯示的方法需要 [int](https://msdn.microsoft.com/library/5kzh1b5w.aspx) 作為輸入引數且會傳回字串︰  
  
[!code-csharp[方法簽章](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
宣告變數之後，不能以新類型重新宣告它，也無法將與所宣告類型不相容的值指派給它。 例如，您無法宣告 [int](https://msdn.microsoft.com/library/5kzh1b5w.aspx) 並將為 [true](https://msdn.microsoft.com/library/06d3w013.aspx) 的布林值指派給它。 不過，可以將值轉換為其他類型，例如，指派給新的變數，或作為方法引數傳遞時。 編譯器會自動執行不會造成資料遺失的「類型轉換」**。 而可能導致資料遺失的轉換在原始程式碼中需要有「轉換」**。 

如需詳細資訊，請參閱[轉換和類型轉換](https://msdn.microsoft.com/library/ms173105.aspx)。
 
## <a name="built-in-types"></a>內建類型
C# 提供一組標準內建數字類型，代表整數、浮點數值、布林運算式、文字字元、十進位值及其他資料型別。 另外還有內建的 **string** 和 **object** 類型。 這些都可供您在任何 C# 程式中使用。 如需內建類型的詳細資訊，請參閱[類型的參考表](https://msdn.microsoft.com/library/1dhd7f2x.aspx)。  
  
## <a name="custom-types"></a>自訂類型  
您可以使用 [struct](https://msdn.microsoft.com/library/ah19swz4.aspx)、[class](https://msdn.microsoft.com/library/0b0thckt.aspx)、[interface](https://msdn.microsoft.com/library/87d83y5b.aspx) 和 [enum](https://msdn.microsoft.com/library/sbbt4032.aspx) 建構來建立您自己的自訂類型。 .NET Framework Class Library 本身是 Microsoft 所提供的自訂類型集合，您可以在自己的應用程式中使用。 根據預設，類別庫中最常使用的類型可用於任何 C# 程式中。 只有當您明確地將專案參考新增至定義所在的組件時，才能使用其他類型。 編譯器在有該組件的參考之後，您可以針對在原始程式碼的該組件中宣告的類型宣告變數 (和常數)。 如需詳細資訊，請參閱 [.NET Framework 類別庫](https://msdn.microsoft.com/library/gg145045(v=vs.110).aspx)。  
  
## <a name="generic-types"></a>泛型類型  
您可以使用一或多個「型別參數」**來宣告類型，作為預留位置 (具象類型**)，以供用戶端程式碼在其建立該類型的執行個體時提供實際類型。 這類的類型稱為「泛型型別」**。 例如，.NET Framework 類型 @System.Collections.Generic.List%601 有一個型別參數，依慣例命名為 *T*。當您建立該類型的執行個體時，您會指定該清單將包含的物件類型，例如 string：  
  
[!code-csharp[泛型型別](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)] 
  
使用型別參數讓您能夠重複使用相同的類別來保存任何項目類型，而不需要將每個項目都轉換為 [object](https://msdn.microsoft.com/library/9kkx3h3c.aspx)。 泛型集合類別則稱為「強型別集合」**，因為編譯器知道集合項目的特定類型，如果您嘗試將整數新增至上一個範例中的 `strings` 物件，便會在編譯時期引發錯誤。 如需詳細資訊，請參閱[泛型](programming-guide/generics/index.md)。 

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>隱含類型、匿名型別和 Tuple 類型  
如先前所述，您可以使用 [var](https://msdn.microsoft.com/library/bb383973.aspx) 關鍵字，隱含地輸入區域變數 (但不是類別成員)。 變數還是會在編譯時期收到類型，但其是由編譯器所提供的類型。 如需詳細資訊，請參閱[隱含類型區域變數](https://msdn.microsoft.com/library/bb384061.aspx)。  
  
在某些情況下，不方便為一組您不想要儲存或在方法界限外傳遞的簡單相關值，建立簡單的具名類型。 為此，您可以建立「匿名型別」**。 如需詳細資訊，請參閱[匿名型別](https://msdn.microsoft.com/library/bb397696.aspx)。

通常會想要從方法傳回多個值。 您可以建立在單一方法呼叫中傳回多個值的「Tuple 類型」**。 如需詳細資訊，請參閱 [Tuple](tuples.md)。

## <a name="the-common-type-system"></a>一般型別系統  
請務必了解 .NET Framework 中有關型別系統的兩個基本概念：  
  
-   它支援繼承準則。 類型可以衍生自稱為「基底類型」**的其他類型。 衍生類型會繼承 (有部分限制) 基底類型的方法、屬性和其他成員。 基底類型同樣可以衍生自一些其他類型，衍生類型則會繼承其繼承階層架構中兩個基底類型的成員。 所有類型 (包括 @System.Int32 這類內建數字類型 (C# 關鍵字：`int`)) 最終衍生自單一基底類型，即 @System.Object (C# 關鍵字：`object`)。 這種統一類型階層架構稱為[一般型別系統](../standard/common-type-system.md) (CTS)。 如需 C# 中有關繼承的詳細資訊，請參閱[繼承](https://msdn.microsoft.com/library/ms173149.aspx)。  
  
-   CTS 中的每個類型都會定義為「實值型別」**或「參考型別」**。 這包括 .NET Framework Class Library 中的所有自訂類型以及您自己的使用者定義型別。 您使用 [struct](https://msdn.microsoft.com/library/ah19swz4.aspx) 關鍵字定義的類型為實值型別；所有內建數字類型都是 **struct**。 如需實值型別的詳細資訊，請參閱[結構](structs.md)。 您使用 [class](https://msdn.microsoft.com/library/0b0thckt.aspx) 關鍵字定義的類型為參考型別。 如需參考型別的詳細資訊，請參閱[類別](classes.md)。 參考型別和實值型別有不同的編譯時期規則和不同的執行階段行為。
 
  
## <a name="see-also"></a>請參閱
[結構](structs.md)

[類別](classes.md)

