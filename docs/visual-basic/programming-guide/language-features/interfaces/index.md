---
title: 介面 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
  - 'Visual Basic code, interfaces'
  - 'interfaces [Visual Basic], Visual Basic'
  - interfaces
  - 'interfaces [Visual Basic]'
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
---
# <a name="interfaces-visual-basic"></a>介面 (Visual Basic)
「介面」可定義類別可實作的屬性、方法和事件。 介面可讓您將功能定義為一小組緊密相關的屬性、方法和事件；這會降低相容性問題，因為您可以為您的介面開發增強的實作，而不會危及現有程式碼。 只要開發額外的介面和實作，您就可以隨時加入新功能。  
  
 另有幾個原因，會讓您想要使用介面而非類別繼承：  
  
-   介面是較適用於，當您的應用程式需要許多可能不相關的物件類型來提供特定功能時。  
  
-   介面比基底類別更有彈性，因為您可以定義可實作多個介面的單一實作。  
  
-   介面較適合不必從基底類別繼承實作的情況。  
  
-   當您無法使用類別繼承時，介面相當有用。 例如，結構不能從類別繼承，但它們可以實作介面。  
  
## <a name="declaring-interfaces"></a>宣告介面  
 介面定義內含於 `Interface` 和 `End Interface` 陳述式之間。 遵循 `Interface` 陳述式，您可以新增選擇性的 `Inherits` 陳述式，其中列出一或多個繼承的介面。 `Inherits` 陳述式必須在宣告中所有其他陳述式之前 (註解除外)。 介面定義中剩餘的陳述式應該是 `Event`、`Sub`、`Function`、`Property`、`Interface`、`Class`、`Structure` 和 `Enum` 陳述式。 介面不能包含任何實作程式碼，或實作程式碼相關聯的陳述式，例如 `End Sub` 或 `End Property`。  
  
 在命名空間中，介面陳述式預設為 `Friend`，但它們也可以明確宣告為 `Public` 或 `Friend`。 類別、模組、介面和結構中定義的介面預設為 `Public`，但它們也可以明確宣告為 `Public`、`Friend`、`Protected` 或 `Private`。  
  
> [!NOTE]
>  `Shadows` 關鍵字可以套用至所有介面成員。 `Overloads` 關鍵字可以套用至介面定義中宣告的 `Sub`、`Function` 和 `Property` 陳述式。 此外，`Property` 陳述式可以有 `Default`、`ReadOnly` 或 `WriteOnly` 修飾詞。 不允許其他修飾詞，即 `Public`、`Private`、`Friend`、`Protected`、`Shared`、`Overrides`、`MustOverride` 或 `Overridable`。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 例如，下列程式碼會定義一個介面，其包含一個函式、一個屬性與一個事件。  
  
 [!code-vb[VbVbalrOOP#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#17)]  
  
## <a name="implementing-interfaces"></a>實作介面  
 Visual Basic 保留字`Implements`用於兩種方式。 `Implements` 陳述式表示類別或結構實作介面。 `Implements` 關鍵字表示類別成員或結構成員實作特定介面成員。  
  
### <a name="implements-statement"></a>Implements 陳述式  
 如果類別或結構實作一或多個介面，它在 `Class` 或 `Structure` 陳述式後面必須緊接著 `Implements` 陳述式。 `Implements` 陳述式需要由類別實作的介面清單 (以逗號分隔)。 類別或結構必須使用 `Implements` 關鍵字實作所有介面成員。  
  
### <a name="implements-keyword"></a>Implements 關鍵字  
  `Implements` 關鍵字需要實作介面成員之逗號分隔清單。 一般而言，只會指定單一介面成員，但您可以指定多個成員。 介面成員的規格包含介面名稱 (必須在類別內的實作陳述式中指定)、句號，以及要實作的成員函式、屬性或事件的名稱。 實作介面成員的成員名稱可以使用任何合法的識別項，並不限於`InterfaceName_MethodName`舊版的 Visual Basic 中使用的慣例。  
  
 例如，下列程式碼顯示如何宣告實作介面的方法、且名為 `Sub1` 的副程式：  
  
 [!code-vb[VbVbalrOOP#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#69)]  
  
 實作成員的參數類型和傳回型別，必須符合介面中的介面屬性或成員宣告。 最常見的實作介面項目的方式是使用與介面同名的成員，如上述範例所示。  
  
 若要宣告介面方法的實作，您可以使用執行個體方法宣告上的任何合法屬性，包括 `Overloads`、`Overrides`、`Overridable`、`Public`、`Private`、`Protected`、`Friend`、`Protected Friend`、`MustOverride`、`Default` 和 `Static`。 `Shared` 屬性無效，因為它會定義類別而非執行個體方法。  
  
 使用 `Implements`，您也可以撰寫單一方法來實作一個介面中定義的多個方法，如下列範例所示：  
  
 [!code-vb[VbVbalrOOP#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#70)]  
  
 您可以使用私用成員來實作介面成員。 當私用成員實作介面的成員時，該成員會經由介面成為可用，即使不是直接在類別的物件變數上使用亦然。  
  
### <a name="interface-implementation-examples"></a>介面實作範例  
 實作介面的類別必須實作其所有屬性、方法和事件。  
  
 下列範例會定義兩個介面。 第二個介面 `Interface2` 繼承 `Interface1`，並定義額外的屬性和方法。  
  
 [!code-vb[VbVbalrOOP#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#39)]  
  
 下一個範例會實作 `Interface1`，即上述範例中定義的介面：  
  
 [!code-vb[VbVbalrOOP#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#40)]  
  
 最後一個範例會實作 `Interface2`，包括繼承自 `Interface1` 的方法：  
  
 [!code-vb[VbVbalrOOP#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#41)]  
  
 您可以使用 readwrite 屬性來實作 readonly 屬性 (也就是您不需要在實作類別中將它宣告為 readonly)。  實作介面保證至少會實作此介面所宣告的成員，但是您可以提供更多功能，例如可讓您使用可寫入的屬性。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[逐步解說：建立和實作介面](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|提供詳細的程序，引導您定義和實作您自己的介面之程序。|  
|[泛型介面中的變異數](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|討論泛型介面中的共變性與逆變性，並提供.NET Framework 中的 Variant 泛型介面清單。|
