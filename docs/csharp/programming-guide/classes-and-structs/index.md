---
title: 類別和結構 (C# 程式設計手冊)
description: 說明類別和結構 (structs) 在 C# 中的用途。
keywords: 類別 (C#), 結構 (C#), 結構 (structs) (C#), 參考型別 (C#), 實值型別 (C#)
ms.date: 01/17/2016
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
caps.latest.revision: 48
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8c4cbbdd0384c0c0e97d6a7c655e798d0562d9a8
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="classes-and-structs-c-programming-guide"></a>類別和結構 (C# 程式設計手冊)
類別和結構是 .NET Framework 中一般型別系統的兩個基本建構。 每一個基本上都是封裝一組屬於相同邏輯單元之資料和行為的資料結構。 資料和行為是類別或結構的「成員」，它們包含類別或結構的方法、屬性和事件等，如本主題稍後所列。  
  
 類別或結構宣告就像是用來在執行階段建立執行個體或物件的藍圖。 如果您定義稱為 `Person` 的類別或結構，`Person` 將會是型別的名稱。 如果您宣告並初始化型別 `Person` 的變數 `p`，`p` 即為 `Person` 的物件或執行個體。 您可以建立多個相同 `Person` 型別的執行個體，且每個執行個體在其屬性與欄位中都可以有不同的值。  
  
 類別是參考型別。 當建立類別的物件時，物件指派至的變數僅會保留該記憶體的參考。 當物件參考指派至新的變數時，新的變數會參考到原始物件。 透過某個變數所做的變更會反映在其他變數中，因為它們都參考相同的資料。  
  
 結構是實值型別。 當建立結構時，結構指派至的變數會保留結構的實際資料。 將結構指派至新的變數時，將會複製結構。 因此，新的變數和原始變數會各自包含一份相同的資料。 針對其中一個複本所做的變更，並不會影響到另一個複本。  
  
 一般情況下，類別會用來建立更複雜行為的模型，或是要在建立類別物件後修改之資料的模型。 結構最適合小型資料結構，該結構主要包含不會在結構建立後修改的資料。  
  
 如需詳細資訊，請參閱[類別](../../../csharp/programming-guide/classes-and-structs/classes.md)、[物件](../../../csharp/programming-guide/classes-and-structs/objects.md)和[結構](../../../csharp/programming-guide/classes-and-structs/structs.md)。  
  
## <a name="example"></a>範例  
 在下列範例中，`ProgrammingGuide` 命名空間中的 `CustomClass` 有三個成員：執行個體建構函式、名稱為 `Number` 的屬性，以及名稱為 `Multiply` 的方法。 `Program` 類別中的 `Main` 方法會建立 `CustomClass` 的執行個體 (物件)，且物件的方法和屬性會透過點標記法來存取。
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>封裝  
 「封裝」有時被稱為物件導向程式設計的第一大支柱或原則。 根據封裝原則，類別或結構可以指定其各個成員針對類別或結構外部之程式碼的存取程度。 不應該在類別或組件之外使用的方法和變數，可隱藏以限制程式碼錯誤或惡意攻擊的可能性。  
  
 如需有關類別的詳細資訊，請參閱[類別](../../../csharp/programming-guide/classes-and-structs/classes.md)和[物件](../../../csharp/programming-guide/classes-and-structs/objects.md)。  
  
### <a name="members"></a>Members  
 所有的方法、欄位、常數、屬性和事件都必須在型別內宣告。這些便是該型別的「成員」。 和部分其他語言不同，在 C# 中並沒有全域變數或方法。 即使是程式的進入點 (`Main` 方法)，也必須在類別或結構內宣告。 下列清單包含所有可能在類別或結構中宣告的各種成員。  
  
-   [欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [常數](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [事件](../../../csharp/programming-guide/events/index.md)  
  
-   [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [索引子](../../../csharp/programming-guide/indexers/index.md)  
  
-   [運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [巢狀型別](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### <a name="accessibility"></a>協助工具選項  
 有些方法和屬性必須從類別或結構以外的程式碼呼叫或存取，它們稱為「用戶端程式碼」。 其他方法和屬性可能只會在類別或結構本身中使用。 請務必限制程式碼的可存取性，以確保只有目標用戶端程式碼可以存取。 您可以使用存取修飾詞 [public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[protected internal](../../../csharp/language-reference/keywords/protected-internal.md)、[private](../../../csharp/language-reference/keywords/private.md) 和 [private protected](../../../csharp/language-reference/keywords/private-protected.md)，來指定用戶端程式碼可以存取您的類型和其成員的程度。 預設可存取性為 `private`。 如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
### <a name="inheritance"></a>繼承  
 類別 (而不是結構) 支援繼承的概念。 衍生自另一個類別 (「基底類別」) 的類別，會自動包含基底類別的所有 public、protected 和 internal 成員 (其建構函式和完成項除外)。 如需詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)和[多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)。  
  
 類別可宣告為[抽象](../../../csharp/language-reference/keywords/abstract.md)，這表示其一或多個方法沒有任何實作。 雖然抽象類別無法直接具現化，但是它們可以做為其他能提供遺失實作之類別的基底類別。 類別也可以宣告為[密封](../../../csharp/language-reference/keywords/sealed.md)，以防止其他類別繼承它們。 如需詳細資訊，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
### <a name="interfaces"></a>介面  
 類別和結構可以繼承多個介面。 繼承介面表示型別會實作介面中定義的所有方法。 如需詳細資訊，請參閱[介面](../../../csharp/programming-guide/interfaces/index.md)。  
  
### <a name="generic-types"></a>泛型型別  
 類別和結構可以使用一或多個型別參數加以定義。 當用戶端程式碼建立型別的執行個體時，便會提供型別。 例如， <xref:System.Collections.Generic> 命名空間中的 <xref:System.Collections.Generic.List%601> 類別是以一個型別參數來定義。 用戶端程式碼會建立 `List<string>` 或 `List<int>` 的執行個體，以指定清單將保留的型別。 如需詳細資訊，請參閱[泛型](../../../csharp/programming-guide/generics/index.md)。  
  
### <a name="static-types"></a>靜態型別  
 類別 (而不是結構) 可以宣告為[靜態](../../../csharp/language-reference/keywords/static.md)。 靜態類別僅可以包含靜態成員，且無法使用新的關鍵字具現化。 類別的其中一個複本會在程式載入時載入至記憶體，其成員會透過類別名稱存取。 類別和結構都可以包含靜態成員。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
### <a name="nested-types"></a>巢狀類型  
 類別或結構能以巢狀方式置於另一個類別或結構內。 如需詳細資訊，請參閱[巢狀型別](../../../csharp/programming-guide/classes-and-structs/nested-types.md)。  
  
### <a name="partial-types"></a>部分型別  
 您可以在某個程式碼檔案中定義類別、結構或方法的某個部分，並在另一個程式碼檔案中定義另一部分。 如需詳細資訊，請參閱[部分類別與方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。  
  
### <a name="object-initializers"></a>物件初始設定式  
 您可以具現化及初始化類別或結構物件，以及物件的集合，而不用明確地呼叫其建構函式。 如需詳細資訊，請參閱[物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
### <a name="anonymous-types"></a>匿名類型  
 在不方便或不必要建立具名類別的情況下 (例如當您使用不必保存或傳遞到另一個方法的資料結構填入清單時)，可以使用匿名型別。 如需詳細資訊，請參閱[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。  
  
### <a name="extension-methods"></a>擴充方法  
 您可以透過建立其方法能以該方法屬於原始型別之方式呼叫的個別型別，在不必建立衍生類別的情況下「擴充」類別。 如需詳細資訊，請參閱[擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。  
  
### <a name="implicitly-typed-local-variables"></a>隱含類型區域變數  
 在類別或結構方法內，您可以使用隱含型別來指示編譯器在編譯時間判斷正確的型別。 如需詳細資訊，請參閱[隱含型別區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)
