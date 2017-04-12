---
title: "Option Infer 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OptionInfer
- vb.Infer
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement
- Infer keyword
- declaring variables, inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
caps.latest.revision: 72
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e6074ad44b94c80f275af562edef2dcd1173c0c3
ms.lasthandoff: 03/13/2017

---
# <a name="option-infer-statement"></a>Option Infer 陳述式
可讓您在宣告變數時使用區域類型推斷。  
  
## <a name="syntax"></a>語法  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`On`|選擇項。 啟用區域類型推斷。|  
|`Off`|選擇項。 停用區域類型推斷。|  
  
## <a name="remarks"></a>備註  
 若要在檔案中設定 `Option Infer`，請在檔案頂端的任何其他原始程式碼之前輸入 `Option Infer On` 或 `Option Infer Off`。 如果在檔案中設定給 `Option Infer` 的值與 IDE 或命令列中設定的值衝突，檔案中的值具有優先權。  
  
 當您將 `Option Infer` 設定為 `On` 時，可以宣告區域變數而不用明確陳述資料類型。 編譯器會從其初始化運算式的類型推斷變數的資料類型。  
  
 在下圖中，`Option Infer` 已開啟。 宣告 `Dim someVar = 2` 中的變數依類型推斷宣告為整數。  
  
 ![宣告的 IntelliSense 檢視。](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")  
Option Infer 開啟時的 IntelliSense  
  
 在下圖中，`Option Infer` 已關閉。 宣告 `Dim someVar = 2` 中的變數依類型推斷宣告為 `Object`。 在此範例中， **Option Strict**設定設為**關閉**上[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。  
  
 ![宣告的 IntelliSense 檢視。](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")  
Option Infer 關閉時的 IntelliSense  
  
> [!NOTE]
>  當變數被宣告為 `Object` 時，執行階段類型可以在程式執行時變更。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]執行作業呼叫*boxing*和*unboxing*之間進行轉換`Object`和數值型別，使得執行速度變慢。 Boxing 和 unboxing 的相關資訊，請參閱[Visual Basic 語言規格](../../../visual-basic/reference/language-specification.md)。  
  
 類型推斷會套用在程序層級，不會套用在類別、結構、模組或介面中的程序之外。  
  
 如需詳細資訊，請參閱[本機的型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>Option Infer 陳述式不存在時  
 如果原始程式碼不包含`Option Infer`陳述式， **Option Infer**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。 使用命令列編譯器時，如果[/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)編譯器選項使用。  
  
#### <a name="to-set-option-infer-in-the-ide"></a>在 IDE 中設定 Option Infer  
  
1.  在**方案總管 中**，選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[NIB︰ 使用專案設計工具管理專案屬性](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)。  
  
2.  按一下 [編譯]**** 索引標籤。  
  
3.  在設定的值**Option infer**方塊。  
  
 當您建立新的專案， **Option Infer**上設定**編譯** 索引標籤設為**Option Infer**中設定**VB 預設值**對話方塊。 若要存取**VB 預設值**對話方塊的 **工具** 功能表上，按一下 **選項**。 在**選項**對話方塊方塊中，展開**專案和方案**，然後按一下  **VB 預設值**。 中的初始預設設定**VB 預設值**是`On`。  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>在命令列上設定 Option Infer  
  
-   包含[/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)編譯器選項，在**vbc**命令。  
  
## <a name="default-data-types-and-values"></a>預設資料類型和值  
 下表說明在 `Dim` 陳述式中指定資料類型和初始設定式的各種組合結果。  
  
|指定了資料類型？|指定了初始設定式？|範例|結果|  
|---|---|---|---|  
|否|否|`Dim qty`|如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。<br /><br /> 如果 `Option Strict` 已開啟，就會發生編譯時期錯誤。|  
|否|是|`Dim qty = 5`|如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。 請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。<br /><br /> 如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。<br /><br /> 如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時期錯誤。|  
|是|否|`Dim qty As Integer`|變數會初始化為資料類型的預設值。 如需詳細資訊，請參閱[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。|  
|是|是|`Dim qty  As Integer = 5`|如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時間錯誤。|  
  
## <a name="example"></a>範例  
 下列範例示範 `Option Infer` 陳述式如何啟用區域類型推斷。  
  
 [!code-vb[VbVbalrTypeInference #&6;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例示範當變數被視為 `Object` 時，執行階段類型可能會不同。  
  
 [!code-vb[VbVbalrTypeInference #&11;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Visual Basic 預設值，專案選項對話方塊](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)   
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
