---
title: "使用屬性 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "get 存取子 [C#]"
  - "屬性 [C#], 關於屬性"
  - "set 存取子 [C#]"
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# 使用屬性 (C# 程式設計手冊)
屬性 \(Property\) 是欄位和方法的綜合體；  如果是物件的使用者，屬性會以欄位出現，存取屬性需要相同的語法。  而對於類別的實作者，屬性則是一或兩個程式碼區塊，代表 [get](../../../csharp/language-reference/keywords/get.md) 存取子 \(Accessor\) 和 \(或\) [set](../../../csharp/language-reference/keywords/set.md) 存取子。  `get` 存取子的程式碼區塊會於讀取屬性時執行，而且 `set` 存取子的程式碼區塊會在指派新值給該屬性時執行。  不含 `set` 存取子的屬性會被視為唯讀，  而不含 `get` 存取子的屬性會被視為唯寫；  同時具有這兩種存取子的屬性則為可讀寫。  
  
 屬性並不會歸類為變數，這點與欄位不同。  因此，您無法將屬性當成 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 參數進行傳遞。  
  
 屬性能有許多用途：可以在允許變更之前驗證資料；可以在實際從其他某些來源 \(例如資料庫\) 擷取資料時，透明地在某一類別上公開資料；也可以在資料變更 \(例如引發事件，或是變更其他欄位的值\) 時採取動作。  
  
 屬性在類別區塊內宣告的方式是指定欄位存取層級、接著指定屬性的型別、再指定屬性的名稱，然後是宣告 `get` 存取子和 \(或\) `set` 存取子的程式碼區塊。  例如：  
  
 [!code-cs[csProgGuideProperties#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_1.cs)]  
  
 在此範例中，`Month` 被宣告為屬性，如此 `set` 存取子即可確保 `Month` 值會設定為 1 到 12 之間。  `Month` 屬性使用私用欄位來追蹤實際的值。  屬性資料的實際位置通常稱為屬性的「支援的存放區」， 屬性經常會使用私用欄位做為支援的存放區，  而欄位之所以標記為私用的原因，是要確保一定要透過呼叫屬性才能夠變更欄位。  如需公用和私用存取限制的詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 自動實作的屬性為簡單屬性宣告提供了簡化的語法。  如需詳細資訊，請參閱[自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。  
  
## get 存取子  
 `get` 存取子的主體就像方法的主體。  它必須傳回屬性型別的值。  執行 `get` 存取子的意思就是等於讀取欄位值；  例如，當您從 `get` 存取子傳回私用變數，並啟用最佳化時，編譯器就會內嵌對 `get` 存取子方法的呼叫，如此即可避免方法呼叫額外負荷。  然而，由於在編譯時期，編譯器不知道在執行階段可以確實呼叫哪些方法，因此，無法內嵌虛擬的 `get` 存取子方法。  下列是一個 `get` 存取子，它會傳回私用欄位 `name` 的值：  
  
 [!code-cs[csProgGuideProperties#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_2.cs)]  
  
 當您參考屬性時，除了指派的目標之外，還會叫用 `get` 存取子來讀取屬性值，  例如：  
  
 [!code-cs[csProgGuideProperties#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_3.cs)]  
  
 `get` 存取子必須在 [return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式結束，而且控制項不能超出存取子的主體。  
  
 使用 `get` 存取子來變更物件狀態是不好的程式設計作法，  例如，每一次存取 `number` 欄位時，下列存取子會造成物件狀態變更的不良結果。  
  
 [!code-cs[csProgGuideProperties#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_4.cs)]  
  
 `get` 存取子可以用於傳回欄位值，或予以計算並且傳回。  例如：  
  
 [!code-cs[csProgGuideProperties#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_5.cs)]  
  
 在之前的程式碼片段中，如果您沒有將值指派給 `Name` 屬性，它會傳回 NA 值。  
  
## set 存取子  
 `set` 存取子就像傳回型別為 [void](../../../csharp/language-reference/keywords/void.md) 的方法。  它使用稱為 `value` 的隱含參數，其型別是屬性的型別。  在下列範例中，會將 `set` 存取子加入 `Name` 屬性：  
  
 [!code-cs[csProgGuideProperties#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_6.cs)]  
  
 當您將值指派給屬性，會以提供新值的引數來叫用 `set` 存取子。  例如：  
  
 [!code-cs[csProgGuideProperties#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_7.cs)]  
  
 在 `set` 存取子中，區域變數宣告使用隱含參數名稱 `value` 是錯誤的。  
  
## 備註  
 屬性可以標記為 `public`、`private`、`protected`、`internal` 或 `protected internal`，  這些存取修飾詞 \(Modifier\) 將定義類別使用者如何存取屬性。  相同屬性的 `get` 和 `set` 存取子可能具有不同的存取修飾詞。  例如，`get` 可能具有 `public`，以允許來自型別外部的唯讀存取，而 `set` 則可能具有 `private` 或 `protected`。  如需詳細資訊，請參閱 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 您可以使用 `static` 關鍵字，將屬性宣告為靜態屬性。  這讓呼叫端即使沒有類別的執行個體，也可以隨時使用屬性。  如需詳細資訊，請參閱 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
 屬性可以使用 [virtual](../../../csharp/language-reference/keywords/virtual.md) 關鍵字標記為虛擬屬性。  如此一來，衍生類別就可以使用 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字覆寫屬性行為。  如需這些選項的詳細資訊，請參閱 [繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。  
  
 用來覆寫虛擬屬性的屬性也可以是 [sealed](../../../csharp/language-reference/keywords/sealed.md)，對於衍生類別來說，該屬性即不再為虛擬的。  最後，屬性可以宣告為 [abstract](../../../csharp/language-reference/keywords/abstract.md)。  這表示類別中不會有實作，而衍生類別必須撰寫本身的實作。  如需這些選項的詳細資訊，請參閱 [抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
> [!NOTE]
>  在 [static](../../../csharp/language-reference/keywords/static.md) 屬性的存取子上，使用 [虛擬](../../../csharp/language-reference/keywords/virtual.md)、[abstract](../../../csharp/language-reference/keywords/abstract.md) 或 [override](../../../csharp/language-reference/keywords/override.md) 修飾詞是錯誤的。  
  
## 範例  
 這個範例示範執行個體、靜態和唯讀屬性；  該屬性會接受從鍵盤輸入的員工名稱、以 1 遞增 `NumberOfEmployees`，及顯示員工名稱和編號。  
  
 [!code-cs[csProgGuideProperties#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_8.cs)]  
  
## 範例  
 這個範例示範如何存取基底類別中的屬性，該屬性被衍生類別中名稱相同的另一個屬性所隱藏。  
  
 [!code-cs[csProgGuideProperties#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_9.cs)]  
  
 以下是上述範例中的重點：  
  
-   衍生類別中的 `Name` 屬性會隱藏基底類別中的 `Name` 屬性，  在這種情況下，`new` 修飾詞是用於衍生類別裡的屬性宣告中：  
  
     [!code-cs[csProgGuideProperties#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_10.cs)]  
  
-   轉換 `(Employee)` 是用來存取基底類別中的隱藏屬性：  
  
     [!code-cs[csProgGuideProperties#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_11.cs)]  
  
     如需隱藏成員的詳細資訊，請參閱 [new 修飾詞](../../../csharp/language-reference/keywords/new-modifier.md)。  
  
## 範例  
 在這個範例裡，`Cube` 和 `Square` 兩個類別會實作 `Shape` 抽象類別 \(Abstract Class\)，並且覆寫它的抽象 `Area` 屬性。  請注意 [override](../../../csharp/language-reference/keywords/override.md) 修飾詞在屬性上的用法。  該程式會接受邊長的輸入值，然後計算正方形和立方體的面積，  而且，還也會接受面積的輸入值，然後計算正方形和立方體的對應邊長。  
  
 [!code-cs[csProgGuideProperties#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_12.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [介面屬性](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)   
 [自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)