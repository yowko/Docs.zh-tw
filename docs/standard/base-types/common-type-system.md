---
title: 一般類型系統
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- type system
- common type system
- assemblies [.NET Framework], types
- reference types
- value types
- cross-language interoperability
- namespaces [.NET Framework], types
- types, about types
ms.assetid: 53c57c96-83e1-4ee3-9543-9ac832671a89
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c8db725e25fe441c875a25cba97eb2090d4c071
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46326656"
---
# <a name="common-type-system"></a>一般類型系統
一般型別系統定義如何在 Common Language Runtime 中宣告、使用和管理型別，同時也是執行階段支援跨語言整合中很重要的一部分。 一般型別系統可執行下列功能：  
  
-   建立利於提供跨語言整合、型別安全 (Type Safety) 和高效能程式碼執行的架構。  
  
-   提供可支援多種程式語言完整實作 (Implementation) 的物件導向模型。  
  
-   定義語言必須遵守的規則，有助於確保以不同語言撰寫的物件可彼此互動。  
  
-   提供包含應用程式開發時使用之原始資料型別 (例如 <xref:System.Boolean>、<xref:System.Byte>、<xref:System.Char>、<xref:System.Int32> 與 <xref:System.UInt64>) 的程式庫。  
  
 此主題包括下列章節：  
  
-   [.NET 中的類型](#types_in_the_net_framework)  
  
-   [型別定義](#type_definitions)  
  
-   [型別成員](#type_members)  
  
-   [類型成員的特性](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>   
## <a name="types-in-net"></a>.NET 中的類型  
 .NET 中的所有型別屬於實值型別或是參考型別。  
  
 如果資料型別的物件是由物件的實際值來表示，那麼這個資料型別就是實值型別。 如果將實值型別的執行個體指派給變數，該變數會取得這個值的全新複本。  
  
 如果資料型別的物件是由物件之實際值的參考 (類似於指標) 來表示，那麼這個資料型別就是參考型別。 如果將參考型別指派給變數，該變數就會參考 (指向) 原始值。 不會進行複製。  
  
 .NET 中的一般型別系統支援下列五種型別：  
  
-   [類別](#Classes)  
  
-   [結構](#Structures)  
  
-   [列舉](#Enumerations)  
  
-   [介面](#Interfaces)  
  
-   [委派](#Delegates)  
  
<a name="Classes"></a>   
### <a name="classes"></a>類別  
 類別是指可以直接衍生自其他類別且隱含衍生自 <xref:System.Object?displayProperty=nameWithType> 的參考型別。 類別會定義物件 (類別的執行個體) 可以執行的作業 (方法、事件或屬性) 以及物件包含的資料 (欄位)。 雖然類別通常包括定義和實作 (不同於介面，例如介面只包含定義而不含實作)，但是類別可以有一個或多個不具實作的成員。  
  
 下表將說明類別可以具有的某些特性。 每一個支援執行階段的語言都會提供一種方式，指出類別或類別成員具有這些其中一個或多個特性。 然而，以 .NET 為目標的程式設計語言則無法使用所有這些特性。  
  
|特性|描述|  
|--------------------|-----------------|  
|sealed|指定無法從這個型別衍生出其他類別。|  
|實作|指出類別會以提供介面成員實作的方式來使用一個或多個介面。|  
|abstract|表示這個類別無法執行個體化。 若要使用這個特性，必須從它衍生出其他類別。|  
|繼承|指出類別的執行個體可用於已指定基底類別 (Base Class) 的任何位置。 從基底類別繼承的衍生類別可以使用基底類別所提供的任何公用成員實作，或者衍生類別可以利用本身的實作來覆寫公用成員的實作。|  
|exported 或 not exported|指出是否可在定義類別的組件中看見類別。 這項特性僅適用於最上層類別，並不適用於巢狀類別。|  
  
> [!NOTE]
>  類別也可以透過巢狀方式置於父類別或結構中。 巢狀類別也具有成員特性。 如需詳細資訊，請參閱[巢狀型別](#NestedTypes)。  
  
 沒有實作的類別成員是抽象成員。 有一個或多個抽象成員的類別本身就是抽象的；所以無法建立它的新執行個體。 有些以執行階段為目標的語言即使沒有任何抽象的成員，也允許您將類別標記為抽象。 當您需要封裝一組衍生類別在適當時可繼承或覆寫的基本功能時，可以使用抽象類別 (Abstract Class)。 非抽象的類別即稱為實體類別 (Concrete Class)。  
  
 一個類別可以實作任意數量的介面，但是除了所有類別都會隱含繼承的來源 <xref:System.Object?displayProperty=nameWithType> 以外，只能繼承一個基底類別。 所有類別都至少必須有一個建構函式，用來初始化類別的新執行個體。 如果您沒有明確定義建構函式，大多數的編譯器會自動提供預設 (無參數) 建構函式。  
  
<a name="Structures"></a>   
### <a name="structures"></a>結構  
 結構是自 <xref:System.ValueType?displayProperty=nameWithType> (衍生自 <xref:System.Object?displayProperty=nameWithType>) 隱含繼承的實質型別。 在表示記憶體需求相當小的實質型別時，以及將值當做傳值參考傳遞給具有強型別參數的方法時，結構將相當實用。 在 .NET 中，會將所有基本資料類型 (<xref:System.Boolean>、<xref:System.Byte>、<xref:System.Char>、<xref:System.DateTime>、<xref:System.Decimal>、<xref:System.Double>、<xref:System.Int16>、<xref:System.Int32>、<xref:System.Int64>、<xref:System.SByte>、<xref:System.Single>、<xref:System.UInt16>、<xref:System.UInt32> 及 <xref:System.UInt64>) 定義為結構。  
  
 與類別一樣，結構會定義資料 (結構的欄位) 以及可以在該資料上定義的作業 (結構的方法)。 這表示您可以在結構上呼叫方法，包括在 <xref:System.Object?displayProperty=nameWithType> 和 <xref:System.ValueType?displayProperty=nameWithType> 類別上定義的虛擬方法，以及在實值型別本身定義的任何方法。 換言之，除了靜態與非靜態方法之外，結構還可以具有欄位、屬性和事件。 您可以建立結構的執行個體，將它們當做參數傳遞，並將它們當做區域變數儲存或將它們儲存到其他實值型別或參考型別的欄位中。 結構也可以實作介面。  
  
 實值型別在許多層面上與類別不同。 首先，雖然它們隱含繼承自 <xref:System.ValueType?displayProperty=nameWithType>，但是卻無法直接繼承自任何型別。 同樣地，所有實值型別都是密封型別，表示無法從中衍生其他型別。 實值型別不需要建構函式。  
  
 對每一個實值型別而言，Common Language Runtime 都提供了對應的 Boxed 型別，這是具有與實值型別相同狀態和行為的類別。 實值型別的執行個體傳遞給接受型別為 <xref:System.Object?displayProperty=nameWithType> 之參數的方法時，會進行 Boxed 處理。 當控制項從接受實質型別做為傳址參數的方法呼叫傳回時，它會 Unboxed (意即由類別的執行個體轉換回實質型別的執行個體)。 需要 Boxed 型別時，有些語言會要求您使用特殊的語法；其他語言則會在需要時自動使用 Boxed 型別。 當您定義實值型別時，會同時定義 Boxed 和 Unboxed 型別。  
  
<a name="Enumerations"></a>   
### <a name="enumerations"></a>列舉  
 列舉 (Enum) 是直接繼承自 <xref:System.Enum?displayProperty=nameWithType> 的實值型別，並且可以為基礎的基本型別數值提供替代名稱。 列舉型別具有名稱、必須為內建帶正負號或不帶正負號之整數型別 (例如 <xref:System.Byte>、<xref:System.Int32> 或 <xref:System.UInt64>) 的基礎型別，以及一組欄位。 欄位為靜態的常值欄位，每一個欄位各代表一個常數。 相同的數值可指定給多個欄位。 發生這種情況時，必須將其中一個數值標記為反映和字串轉換的主要列舉值。  
  
 您可以將基礎型別的值指定給列舉型別，反之亦然 (Runtime 不需要轉型)。 您可以建立列舉的執行個體，然後呼叫 <xref:System.Enum?displayProperty=nameWithType> 的方法以及在列舉的基礎型別上定義的任何方法。 但是，在需要基礎型別的執行個體時，有些語言可能不允許您將列舉型別當成參數傳遞，反之亦然。  
  
 下列限制適用於列舉型別：  
  
-   不能定義自己的方法。  
  
-   不能實作介面。  
  
-   不能定義屬性或事件。  
  
-   除非是巢狀置於泛型型別中，否則不能是泛型。 換句話說，列舉型別不能有自己的型別參數。  
  
    > [!NOTE]
    >  使用 Visual Basic、C# 和 C++ 建立的巢狀型別 (包括列舉型別) 包含所有封入泛型型別的型別參數，因此，即使沒有自己的型別參數，仍舊是泛型型別。 如需詳細資訊，請參閱 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 參考主題中的＜巢狀型別＞。  
  
 <xref:System.FlagsAttribute> 屬性代表一種特殊的列舉型別，稱為位元欄位 (Bit Field)。 Runtime 本身無法區別傳統列舉型別和位元欄位，但是您所使用的語言或許可以區分出來。 在區分時，可在位元欄位上使用位元 (Bitwise) 運算子來產生未命名的數值，但是不能用於列舉型別。 列舉型別通常用於唯一的項目 (Element) 清單，例如該星期的天數、國別或區域名稱等。 位元欄位通常用於可能以組合形式出現的特性或數量清單，例如 `Red And Big And Fast`。  
  
 下列範例顯示如何使用位元欄位和傳統列舉型別。  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>介面  
 介面會定義指定「可以執行」關聯性 (Relationship) 或「擁有」關聯性的合約。 介面常用來實作功能，例如比較和排序 (<xref:System.IComparable> 和 <xref:System.IComparable%601> 介面)、測試是否相等 (<xref:System.IEquatable%601> 介面)，或列舉集合中的項目 (<xref:System.Collections.IEnumerable> 和 <xref:System.Collections.Generic.IEnumerable%601> 介面)。 介面可以擁有屬性、方法和事件，這些都是抽象成員，也就是說，雖然介面會定義成員及其簽章，但每個介面成員的功能則是由實作介面的型別所定義。 這表示，實作介面的任何類別或結構都必須為介面中宣告的抽象成員提供定義。 介面可能會要求任何實作類別或結構也必須實作一個或多個其他介面。  
  
 下列限制適用於介面：  
  
-   介面可宣告為任何存取範圍，但是介面成員必須全部具有公用存取範圍。  
  
-   介面無法定義建構函式。  
  
-   介面不能定義欄位。  
  
-   介面可以只定義執行個體成員， 不能定義靜態成員。  
  
 由於可以使用相同簽章宣告成員的介面不只一個，而且這些成員可以具有分開的實作，因此每一種語言都必須提供規則，將實作對應到需要成員的介面。  
  
<a name="Delegates"></a>   
### <a name="delegates"></a>委派  
 委派是參考型別，用途與 C++ 中的函式指標類似。 委派是用於 .NET 中的事件處理常式和回呼函式。 不同於函式指標，委派更具安全性、可以驗證，而且是型別安全 (Type Safe) 的。 委派型別可以代表具有相容簽章的執行個體方法或靜態方法。  
  
 如果委派參數的型別比方法參數的型別更嚴格，則委派的參數與對應的方法參數相容，因為這樣可保證傳遞給委派的引數能夠安全地傳遞給方法。  
  
 同樣的，如果方法的傳回型別比委派的傳回型別更具限制性，由於此保證方法傳回的值會安全地轉換為委派的傳回型別，委派的傳回型別就會相容於方法的傳回型別。  
  
 例如，具有 <xref:System.Collections.IEnumerable> 型別參數和 <xref:System.Object> 傳回型別的委派，即可代表具有 <xref:System.Object> 型別參數和 <xref:System.Collections.IEnumerable> 型別傳回值的方法。 如需詳細資訊和範例程式碼，請參閱 <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>。  
  
 委派會繫結到其所代表的方法。 除了繫結到方法以外，委派還可以繫結到物件。 物件表示方法的第一個參數，而且每一次叫用委派時，都會傳遞給方法。 如果方法是執行個體方法，那麼繫結物件會傳遞做為隱含的 `this` 參數 (Visual Basic 中則為 `Me`)；如果是靜態方法，物件會傳遞做為方法的第一個正式參數，而且委派簽章必須符合其餘參數。 如需詳細資訊和範例程式碼，請參閱 <xref:System.Delegate?displayProperty=nameWithType>。  
  
 所有的委派都繼承自 <xref:System.MulticastDelegate?displayProperty=nameWithType>，該項則繼承自 <xref:System.Delegate?displayProperty=nameWithType>。 C#、Visual Basic 和 C++ 語言並不允許從這些型別繼承， 而是提供關鍵字以宣告委派。  
  
 由於委派繼承自 <xref:System.MulticastDelegate>，所以委派會具有引動過程清單，這是委派所代表方法的清單，在叫用 (Invoke) 委派時就會執行這些方法。 清單中的所有方法都會接收到叫用委派時所提供的引數。  
  
> [!NOTE]
>  在引動過程清單中具有一個以上方法的委派，即使擁有傳回型別，其傳回值也不會具有定義。  
  
 在許多情況下，例如回呼方法中，委派只代表一個方法，而且您所需要採取的動作，就是建立委派然後再叫用委派。  
  
 對於代表多個方法的委派，.NET 會提供 <xref:System.Delegate> 和 <xref:System.MulticastDelegate> 委派類別的方法，來支援將方法加入至委派引動清單 (<xref:System.Delegate.Combine%2A?displayProperty=nameWithType> 方法)、移除方法 (<xref:System.Delegate.Remove%2A?displayProperty=nameWithType> 方法)，以及取得引動清單 (<xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> 方法) 等諸如此類的作業。  
  
> [!NOTE]
>  在 C#、C++ 和 Visual Basic 中，並不需要對事件處理常式委派使用這些方法，因為這些語言都提供加入和移除事件處理常式的語法。  
  
 
  
<a name="type_definitions"></a>   
## <a name="type-definitions"></a>類型定義  
 型別定義包括下列：  
  
-   在型別上定義的任何屬性 (Attribute)  
  
-   型別的存取範圍 (可視性)  
  
-   型別的名稱  
  
-   型別的基底型別  
  
-   由型別實作的任何介面  
  
-   型別中每一個成員的定義  
  
### <a name="attributes"></a>屬性  
 屬性提供了其他的使用者定義中繼資料。 最常見的屬性用法是，用來將關於型別的其他資訊儲存在組件中，或者在設計階段或執行階段環境中修改型別成員的行為。  
  
 屬性本身都是繼承自 <xref:System.Attribute?displayProperty=nameWithType> 的類別。 每一種支援使用屬性的語言都有自己的語法，用於將屬性套用至語言項目。 屬性可以幾乎套用至所有語言項目，而可以套用屬性的特定項目是由套用到該屬性類別的 <xref:System.AttributeUsageAttribute> 定義。  
  
### <a name="type-accessibility"></a>型別存取範圍  
 所有型別都具有修飾詞 (Modifier)，負責控制其他型別的存取範圍。 下表說明執行階段所支援的型別存取範圍。  
  
|協助工具選項|描述|  
|-------------------|-----------------|  
|public|型別可供所有組件存取|  
|組件|型別只能在本身的組件中存取|  
  
 巢狀型別的存取範圍是依據其存取範圍定義域，由成員的宣告存取範圍和立即包含型別的存取範圍定義域來決定。 但是，巢狀型別的存取範圍領域不能超過包含型別 (Containing Type) 的存取範圍領域。  
  
 在程式 `M` 的型別 `T` 中宣告的巢狀成員 `P`，它的存取範圍領域定義如下 (請注意，`M` 本身也可能是型別)：  
  
-   如果 `M` 的宣告存取範圍是 `public`，`M` 的存取範圍領域就是 `T` 的存取範圍領域。  
  
-   如果 `M` 的宣告存取範圍是 `protected internal`，`M` 的存取範圍領域是 `T` 的存取範圍領域與 `P` 的程式文字和從 `T` 以外宣告的 `P` 所衍生任何型別的程式文字的交集。  
  
-   如果 `M` 的宣告存取範圍是 `protected`，`M` 的存取範圍領域是 `T` 的存取範圍領域與 `T` 的程式文字和 `T` 所衍生之任一型別的交集。  
  
-   如果 `M` 的宣告存取範圍是 `internal`，`M` 的存取範圍領域是 `T` 的存取範圍領域與 `P` 的程式文字的交集。  
  
-   如果 `M` 的宣告存取範圍是 `private`，`M` 的存取範圍領域就是 `T` 的程式文字。  
  
### <a name="type-names"></a>類型名稱  
 一般型別系統對於名稱只有兩項限制：  
  
-   所有名稱都是以 Unicode (16 位元) 字元字串的方式編碼。  
  
-   名稱的內嵌 (16 位元) 值不允許為 0x0000。  
  
 然而，大部分語言會對型別名稱強制執行其他限制。 所有比較都是以位元組為基礎，因此會區分大小寫，而且與地區設定無關 (Locale-Independent)。  
  
 雖然型別可能會參考其他模組和組件中的型別，但是型別必須在一個 .NET 模組中完整定義 (不過根據編譯器的支援，它可以分割成多個原始程式碼檔)。只有在命名空間中的型別名稱才必須是唯一的。 若要能完整辨認型別，必須以包含型別實作的命名空間來限定型別名稱。  
  
### <a name="base-types-and-interfaces"></a>基底型別和介面  
 型別可繼承其他型別的數值和行為。 一般型別系統不允許型別繼承一個以上的基底型別。  
  
 型別可實作任意數目的介面。 若要實作介面，型別必須實作該介面的所有虛擬成員。 虛擬方法可由衍生型別 (Derived Type) 實作，並且可以用靜態或動態方式叫用 (Invoke)。  
  
  
  
<a name="type_members"></a>   
## <a name="type-members"></a>型別成員  
 執行階段允許您定義能夠指定型別行為與狀態的型別成員。 型別成員包含下列：  
  
-   [欄位](#Fields)  
  
-   [屬性](#Properties)  
  
-   [方法](#Methods)  
  
-   [建構函式](#Constructors)  
  
-   [事件](#Events)  
  
-   [巢狀類型](#NestedTypes)  
  
<a name="Fields"></a>   
### <a name="fields"></a>欄位  
 欄位會描述並包含型別狀態組件。 欄位可為執行階段支援的任何型別。 最常見的情形是，欄位為 `private` 或 `protected`，如此才能夠只在類別內部或從衍生類別存取這些欄位。 如果欄位的值可以本身型別以外進行修改，則通常會使用屬性集存取子。 公開欄位通常是唯讀的，而且可以是下兩種型別：  
  
-   常數，它的值是在設計階段指派。 雖然並不會使用 `static` (Visual Basic 中則為 `Shared`) 關鍵字定義，但是這些常數都是類別的靜態成員。  
  
-   唯讀變數，其值可以在類別建構函式中進行指派。  
  
 下列範例說明兩種唯讀欄位的使用方法。  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>   
### <a name="properties"></a>屬性  
 屬性會為型別的值或狀態命名，並且定義用來取得或設定屬性值的方法。 屬性可以是基本型別、基本型別的集合、使用者定義型別或使用者定義型別的集合。 屬性通常是用來保持型別的公用 (Public) 介面與型別的實際表示相互獨立。 這可以讓屬性反映並不直接儲存於類別中的值 (例如，屬性傳回已計算的值時)，或者在值指派給私用欄位之前先執行驗證。 下列範例說明第二種模式。  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 除了含有屬性本身之外，包含可讀取屬性之類型的 Microsoft Intermediate Language (MSIL) 也含有 `get_`*propertyname* 方法，而包含可寫入屬性之型別的 MSIL 則含有 `set_`*propertyname* 方法。  
  
<a name="Methods"></a>   
### <a name="methods"></a>方法  
 方法會描述可以在類型上執行的作業。 方法的簽章會指定所有參數和傳回值可使用的型別。  
  
 雖然大部分方法都會針對方法呼叫定義所需的精確參數數目，但有些方法可支援數目不定的參數。 這些方法最後一個宣告的參數是以 <xref:System.ParamArrayAttribute> 屬性標記。 語言編譯器通常會提供關鍵字，例如 C# 中的 `params` 和 Visual Basic 中的 `ParamArray`，如此便不需要明確使用 <xref:System.ParamArrayAttribute>。  
  
<a name="Constructors"></a>   
### <a name="constructors"></a>建構函式  
 建構函式是一種特殊方法，它會建立類別或結構的新執行個體。 與其他任何方法一樣，建構函式可以包含參數，不過建構函式沒有傳回值，換言之，它們傳回 `void`。  
  
 如果類別的原始程式碼沒有明確定義建構函式，則編譯器會包含預設 (無參數) 建構函式。 不過，如果類別的原始程式碼只定義參數化建構函式，Visual Basic 和 C# 編譯器並不會產生無參數建構函式。  
  
 如果結構的原始程式碼定義建構函式，它們必須是參數化建構函式；結構無法定義預設 (無參數) 建構函式，而且編譯器不會產生結構或其他實值型別的無參數建構函式。 所有實值型別都有隱含的預設建構函式。 這個建構函式是由 Common Language Runtime 實作，會將結構的所有欄位初始化為其預設值。  
  
<a name="Events"></a>   
### <a name="events"></a>事件  
 事件 (Event) 會定義可以回應的事件 (Incident)，並且定義用於訂閱、取消訂閱和產生事件 (Event) 的方法。 事件通常是用來通知其他型別有狀態變更。 如需詳細資訊，請參閱[事件](../../../docs/standard/events/index.md)。  
  
<a name="NestedTypes"></a>   
### <a name="nested-types"></a>巢狀類型  
 巢狀型別是一種型別，它是某個其他型別的成員。 巢狀型別應該緊密地與其包含型別結合，且不能與一般用途的型別一樣實用。 當宣告的型別使用及建立巢狀型別的執行個體時，巢狀型別會很有用處，且不會在公用成員中公開此巢狀型別的使用。  
  
 巢狀型別對於一些開發人員來說可能會覺得混淆，所以除非有強制性的理由，否則不應該讓巢狀型別公開可見。 在設計完善的程式庫中，開發人員應極少使用巢狀型別來將物件執行個體化或宣告變數。  
  
  
  
<a name="characteristics_of_type_members"></a>   
## <a name="characteristics-of-type-members"></a>型別成員的特性  
 一般型別系統允許型別成員具有各種特性，但是所使用的語言並不需要支援所有特性。 下表將描述成員特性。  
  
|特性|適用於|描述|  
|--------------------|------------------|-----------------|  
|abstract|方法、屬性和事件|型別不提供方法的實作。 繼承或實作抽象方法的型別必須提供方法的實作。 唯一的例外狀況 (Exception) 是當衍生型別本身也是抽象型別時。 所有抽象方法都是虛擬的。|  
|private、family、assembly、family 和 assembly、family 或 assembly 或是 public|全部|定義成員的存取範圍：<br /><br /> private<br /> 只能在與成員相同的型別或巢狀型別中存取。<br /><br /> family<br /> 可在與成員相同的型別和從它繼承而來的衍生型別中存取。<br /><br /> 組件<br /> 只能在已定義型別的組件中存取。<br /><br /> family 和 assembly<br /> 只能從同時限定家族和組件存取的型別中存取。<br /><br /> family 或 assembly<br /> 只能從限定家族或組件之一存取的型別中存取。<br /><br /> public<br /> 可從任何型別中存取。|  
|final|方法、屬性和事件|在衍生型別中無法覆寫虛擬方法。|  
|initialize-only|欄位|只能初始化數值，在初始化之後即無法寫入。|  
|執行個體|欄位、方法、屬性和事件|如果成員未標記為 `static` (C# 和 C++)、`Shared` (Visual Basic)、`virtual` (C# 和 C++) 或 `Overridable` (Visual Basic)，則為執行個體成員 (沒有 instance 關鍵字)。 在記憶體中，這類成員的複本數與使用它的物件數一樣。|  
|常值|欄位|指定給欄位的數值是在編譯時間得知的內建實值型別的固定值。 常值 (Literal) 欄位有時候也稱為常數。|  
|newslot 或 override|全部|定義成員與具有相同簽章的繼承成員之間的互動方式：<br /><br /> newslot<br /> 隱藏具有相同簽章的繼承成員。<br /><br /> 覆寫<br /> 取代繼承虛擬方法的定義。<br /><br /> 預設值為 newslot。|  
|靜態|欄位、方法、屬性和事件|成員屬於定義於其上的型別，而非屬於特定的型別執行個體；即使沒有建立型別執行個體，成員仍然存在，而且供型別的所有執行個體共用。|  
|虛擬|方法、屬性和事件|方法可由衍生型別實作，而且可以用靜態或動態方式叫用。 如果使用動態引動，在執行時期進行呼叫的執行個體型別會決定呼叫哪一個方法實作，而不是由編譯時間得知的型別決定。 若要用靜態方式叫用虛擬方法，可能必須將變數轉型為使用方法所需版本的型別。|  
  
### <a name="overloading"></a>多載化  
 每一個型別成員都具有唯一 (Unique) 的簽章。 方法簽章包含方法名稱和參數清單 (方法引數的順序和型別)。 只要簽章不相同，就可以在型別中定義具有相同名稱的多個方法。 定義兩個或多個具有相同名稱的方法時，就說這個方法是多載。 例如在 <xref:System.Char?displayProperty=nameWithType> 中，會多載 <xref:System.Char.IsDigit%2A> 方法。 其中一個方法採用 <xref:System.Char>， 另一個方法則採用 <xref:System.String> 與 <xref:System.Int32>。  
  
> [!NOTE]
>  傳回型別並不會視為方法簽章的一部分。 換言之，如果這些方法的差異只在於傳回型別，就不能多載這些方法。  
  
### <a name="inheriting-overriding-and-hiding-members"></a>繼承、覆寫和隱藏成員  
 衍生型別會繼承其基底型別的所有成員；也就是說，在衍生型別上會定義這些成員，並供衍生型別使用。 繼承成員的行為或品質可用下列兩種方式來修改：  
  
-   衍生型別可用相同的簽章定義新的成員，如此便可隱藏繼承的成員。 您可以將原先為 public 的成員設為 private 成員，或是為標記為 `final` 的繼承方法定義新的行為。  
  
-   衍生型別可覆寫繼承的虛擬方法。 覆寫方法會提供新的方法定義，叫用方法時將根據執行時期的實值型別，而非根據編譯時間得知的變數型別。 只有當虛擬方法未標記為 `final`，而且新的方法至少可像虛擬方法一樣存取時，方法才可覆寫虛擬方法。  
  
## <a name="see-also"></a>另請參閱

- [.NET API 瀏覽器](/dotnet/api)  
- [通用語言執行平台](../../../docs/standard/clr.md)  
- [.NET 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)
