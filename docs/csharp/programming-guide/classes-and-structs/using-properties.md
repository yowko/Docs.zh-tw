---
title: 使用屬性 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: f10f9aa17adf9a03b9b8905245983bdd9d865e39
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200386"
---
# <a name="using-properties-c-programming-guide"></a>使用屬性 (C# 程式設計手冊)
屬性會合併欄位和方法的各個層面。 對物件的使用者而言，屬性會呈現為欄位，而存取屬性需要相同的語法。 對於類別的實作器而言，屬性是一或兩個程式碼區塊，代表 [get](../../../csharp/language-reference/keywords/get.md) 存取子和 (或) [set](../../../csharp/language-reference/keywords/set.md) 存取子。 讀取屬性時，會執行 `get` 存取子的程式碼區塊；指派屬性的新值時，會執行 `set` 存取子的程式碼區塊。 沒有 `set` 存取子的屬性會視為唯讀。 沒有 `get` 存取子的屬性則視為唯寫。 具有這兩個存取子的屬性是讀寫。  
  
 與欄位不同，屬性不會分類為變數。 因此，您無法將屬性傳遞為 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數。  
  
 屬性有許多用途：它們可以先驗證資料，再允許變更；它們會以透明方式公開類別上的資料，而該資料實際是從某個其他來源 (例如資料庫) 所擷取；資料變更時 (例如，引發事件，或變更其他欄位的值)，它們可以採取動作。  
  
 在類別區塊中宣告屬性的方式是指定欄位存取層級，其後依序接著屬性類型、屬性名稱，以及宣告 `get` 存取子和 (或) `set` 存取子的程式碼區塊。 例如：  
  
 [!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]  
  
 在此範例中，將 `Month` 宣告為屬性，因此，`set` 存取子可以確定設定的 `Month` 值介於 1 與 12 之間。 `Month` 屬性使用私用欄位來追蹤實際值。 屬性資料的實際位置通常稱為屬性的「備份存放區」。 屬性經常使用私用欄位作為備份存放區。 此欄位標示為私用，以確認只有呼叫屬性才能進行變更。 如需公用和私用存取限制的詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 自動實作屬性提供簡單屬性宣告的簡化語法。 如需詳細資訊，請參閱[自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。  
  
## <a name="the-get-accessor"></a>get 存取子  
 `get` 存取子的主體與方法的主體類似。 它必須傳回屬性類型的值。 執行 `get` 存取子相當於讀取欄位的值。 例如，當您要從 `get` 存取子傳回私用變數並啟用最佳化時，則編譯器會內嵌 `get` 存取子方法呼叫，因此沒有任何方法呼叫額外負荷。 不過，因為編譯器在編譯時間不知道執行階段實際呼叫的方法，所以無法內嵌虛擬 `get` 存取子方法。 下列 `get` 存取子會傳回私用欄位 `name` 的值：  
  
 [!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]  
  
 當您參考指派目標以外的屬性時，會叫用 `get` 存取子來讀取屬性的值。 例如：  
  
 [!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]  
  
 `get` 存取子必須結束於 [return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式，而且控制無法離開存取子主體。  
  
 這是使用 `get` 存取子變更物件狀態的不良程式設計樣式。 例如，下列存取子會產生每次存取 `number` 欄位時都變更物件狀態的副作用。  
  
 [!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]  
  
 `get` 存取子可用來傳回欄位值或計算它，並傳回它。 例如：  
  
 [!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]  
  
 在先前的程式碼區段中，如果您未指派 `Name` 屬性的值，則會傳回 NA 值。  
  
## <a name="the-set-accessor"></a>set 存取子  
 `set` 存取子與傳回型別為 [void](../../../csharp/language-reference/keywords/void.md) 的方法類似。 它使用稱為 `value` 的隱含參數，其類型為屬性的類型。 在下列範例中，將 `set` 存取子新增至 `Name` 屬性：  
  
 [!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]  
  
 當您指派屬性的值時，會使用提供新值的引數來叫用 `set` 存取子。 例如：  
  
 [!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]  
  
 在 `set` 存取子中使用區域變數宣告的隱含參數名稱 `value` 是錯誤的。  
  
## <a name="remarks"></a>備註  
 屬性可標記為 `public`、`private`、`protected`、`internal`、`protected internal` 或 `private protected`。 這些存取修飾詞定義類別使用者如何存取屬性。 相同屬性的 `get` 和 `set` 存取子可能會有不同的存取修飾詞。 例如，`get` 可能是 `public` 以允許從類型外部進行唯讀存取，而 `set` 可能是 `private` 或 `protected`。 如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 屬性可以使用 `static` 關鍵字宣告為靜態屬性。 這可隨時向呼叫者提供屬性，即使沒有任何類別執行個體也是一樣。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
 屬性可以使用 [virtual](../../../csharp/language-reference/keywords/virtual.md) 關鍵字標示為虛擬屬性。 這可讓衍生類別使用 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字覆寫屬性行為。 如需這些選項的詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。  
  
 覆寫虛擬屬性的屬性也可為 [sealed](../../../csharp/language-reference/keywords/sealed.md)，指定它對衍生類別而言不再是虛擬。 最後，屬性可以宣告為 [abstract](../../../csharp/language-reference/keywords/abstract.md)。 這表示類別中沒有任何實作，而且衍生類別必須撰寫自己的實作。 如需這些選項的詳細資訊，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
> [!NOTE]
>  在 [static](../../../csharp/language-reference/keywords/static.md) 屬性的存取子上使用 [virtual](../../../csharp/language-reference/keywords/virtual.md)、[abstract](../../../csharp/language-reference/keywords/abstract.md) 或 [override](../../../csharp/language-reference/keywords/override.md) 修飾詞是錯誤的。  
  
## <a name="example"></a>範例  
 此範例示範執行個體、靜態和唯讀屬性。 它會從鍵盤接受員工姓名、將 `NumberOfEmployees` 增加 1，並顯示員工姓名和編號。  
  
 [!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]  
  
## <a name="example"></a>範例  
 此範例示範如何存取基底類別中由衍生類別中同名的另一個屬性所隱藏的屬性。  
  
 [!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]  
  
 上述範例中的重點如下：  
  
-   衍生類別中的 `Name` 屬性會隱藏基底類別中的 `Name` 屬性。 在這類情況下，`new` 修飾詞用在衍生類別的屬性宣告中：  
  
     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  
  
-   轉型 `(Employee)` 用來存取基底類別中的隱藏屬性：  
  
     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]  
  
     如需隱藏成員的詳細資訊，請參閱 [new 修飾詞](../../../csharp/language-reference/keywords/new-modifier.md)。  
  
## <a name="example"></a>範例  
 在此範例中，`Cube` 和 `Square` 這兩個類別會實作抽象類別 `Shape`，並覆寫其抽象 `Area` 屬性。 請注意如何在屬性上使用 [override](../../../csharp/language-reference/keywords/override.md) 修飾詞。 程式接受這端作為輸入，並計算正方形和立方體的區域。 它也接受區域作為輸入，並計算正方形和立方體的對應端。  
  
 [!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [介面屬性](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)
- [自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)
