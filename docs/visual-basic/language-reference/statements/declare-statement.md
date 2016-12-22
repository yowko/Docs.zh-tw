---
title: "Declare Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Declare"
  - "vb.Lib"
  - "vb.Any"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Lib keyword"
  - "declaring procedures, Declare statement"
  - "functions [Visual Basic], function procedures"
  - "declarations, procedures"
  - "procedures, declaration"
  - "procedures, external"
  - "Alias keyword"
  - "external references, Visual Basic"
  - "DLLs, declaring procedures"
  - "Declare statement"
  - "declarations, external"
  - "Visual Basic code, Function procedures"
  - "As keyword, in Declare statement"
  - "resources [Visual Basic], declaring"
  - "Public keyword, Declare statement"
  - "platform invoke, Visual Basic external references"
  - "Sub procedures, declarations"
  - "APIs, declaring API functions"
  - "Visual Basic code, Sub procedures"
  - "Function procedures, declaring"
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declare Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

宣告在外部檔案中所實作之程序的參考。  
  
## 語法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ]  
' -or-  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`attributelist`|選擇項。  請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|選擇項。  可以是下列其中一項：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇項。  請參閱 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`charsetmodifier`|選擇項。  指定字元集 \(Character Set\) 和檔案搜尋資訊。  可以是下列其中一項：<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) \(預設值\)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Auto](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|選擇項，但必須出現 `Sub` 或 `Function`。  表示外部程序不會傳回值。|  
|`Function`|選擇項，但必須出現 `Sub` 或 `Function`。  表示外部程序會傳回值。|  
|`name`|必要項。  這個外部參考的名稱。  如需詳細資訊，請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Lib`|必要項。  引入 `Lib` 子句，此子句可識別包含外部程序的外部檔案 \(DLL 或程式碼資源\)。|  
|`libname`|必要項。  包含所宣告程序的檔案名稱。|  
|`Alias`|選擇項。  表示所宣告的程序在其檔案內無法按 `name` 所指定的名稱加以識別。  您可以在 `aliasname` 中指定其識別。|  
|`aliasname`|如果使用 `Alias` 關鍵字，則為必要項。  以下列其中一種方法識別程序的字串：<br /><br /> 程序在其檔案內的進入點 \(Entry Point\) 名稱，位於引號 \(`""`\) 內<br /><br /> \-或\-<br /><br /> 後面接著整數的數字符號 \(`#`\)，這個整數會指定程序進入點在其檔案內的序號 \(Ordinal Number\)|  
|`parameterlist`|如果程序採用參數，則為必要項。  請參閱 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`returntype`|如果已指定 `Function`，且 `Option Strict` 為 `On`，則為必要項。  程序所傳回之值的資料型別。|  
  
## 備註  
 您有時會需要呼叫在專案外的檔案 \(如 DLL 或程式碼資源區\) 中所定義的程序。  當您這麼做的時候，Visual Basic 編譯器 \(Compiler\) 無權存取正確呼叫程序所需的資訊，如程序所在位置、識別它的方式、其呼叫順序 \(Calling Sequence\) 和傳回型別，以及它所使用的字串字元集 \(Character Set\)。  `Declare` 陳述式會建立外部程序的參考，並提供這項必要資訊。  
  
 只能在模組層級使用 `Declare`。  這表示外部參考的「*宣告內容*」必須為類別、結構或模組，而不能是原始程式檔 \(Source File\)、命名空間 \(Namespace\)、介面、程序或區塊。  如需詳細資訊，請參閱[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 外部參考會預設值為 [Public](../../../visual-basic/language-reference/modifiers/public.md) 存取。  您可以使用存取修飾詞調整存取層級。  
  
## 規則  
  
-   **屬性** ：您可以將屬性套用到外部參考。  所套用的屬性只會在您的專案中有作用，在外部檔案中則無作用。  
  
-   **修飾詞。** 外部程序會隱含地 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)。  在宣告外部參考時，您無法使用 `Shared` 關鍵字，因此您無法變更其共用狀態。  
  
     外部程序無法參與覆寫、實作介面成員或處理事件。  因此，您無法在 `Declare` 陳述式 \(Statement\) 中使用 `Overrides`、`Overridable`、`NotOverridable`、`MustOverride`、`Implements` 或 `Handles` 關鍵字。  
  
-   **外部程序名稱** 您給與這個外部參考的名稱 \(在 `name` 中\) 不必與其外部檔案 \(`aliasname`\) 內程序的進入點 \(Entry Point\) 名稱相同。  您可以使用 `Alias` 子句，指定進入點名稱。  如果外部程序與 Visual Basic 保留修飾詞 \(Modifier\) 同名，或與相同範圍中的變數、程序或任何其他程式設計項目同名，這麼做會很有用。  
  
    > [!NOTE]
    >  大部分 DLL 中的進入點名稱都會區分大小寫。  
  
-   **外部程序號碼** 此外，您可以使用 `Alias` 子句，指定外部檔案匯出資料表內之進入點的序號 \(Ordinal Number\)。  若要這麼做，您可以使用數字符號 \(`#`\) 做為 `aliasname` 的開頭。  如果 Visual Basic 不允許外部程序名稱中的任何字元，或如果外部檔案匯出沒有名稱的程序，這麼做會很有用。  
  
## 資料型別規則  
  
-   **參數資料型別：** 如果 `Option Strict` 為 `On`，您必須指定 `parameterlist` 中每一個參數的資料型別。  這可以是任何資料型別，或列舉型別、結構、類別或介面的名稱。  在 `parameterlist` 中，您可以使用 `As` 子句，指定要傳遞至每一個參數之引數的資料型別。  
  
    > [!NOTE]
    >  如果未針對 .NET Framework 撰寫外部程序，您必須注意資料型別要對應。  例如，如果您利用 `Integer` 參數 \(在 Visual Basic 6.0 中為 16 位元\) 宣告 Visual Basic 6.0 程序的外部參考，則必須將對應引數識別為 `Declare` 陳述式中的 `Short`，因為那是 Visual Basic 中的 16 位元整數值。  同樣地，`Long` 在 Visual Basic 6.0 中具有不同的資料寬度，而且會以不同的方式實作 `Date`。  
  
-   **傳回資料型別** 如果外部程序是 `Function`，且 `Option Strict` 為 `On`，則您必須指定已傳回給呼叫程式碼之值的資料型別。  這可以是任何資料型別，或列舉型別、結構、類別或介面的名稱。  
  
    > [!NOTE]
    >  Visual Basic 編譯器並不會驗證您的資料型別是否與外部程序的資料型別相容。  如果不符，Common Language Runtime 會在執行階段產生 <xref:System.Runtime.InteropServices.MarshalDirectiveException> 例外狀況。  
  
-   **預設資料型別** 如果 `Option Strict` 為 `Off`，且您未指定 `parameterlist` 中參數的資料型別，則 Visual Basic 編譯器會將對應引數轉換為 [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)。  同樣地，如果您未指定 `returntype`，則編譯器會採用傳回資料型別做為 `Object`。  
  
    > [!NOTE]
    >  因為您所處理的外部程序可能是在不同平台上撰寫，所以對資料型別做出任何假設或允許它們成為預設值是危險的作法。  指定每一個參數和傳回值的資料型別 \(如果有的話\) 是較為安全的作法。  這也會增進程式碼的可讀性。  
  
## 行為  
  
-   **範圍。** ：外部參考的類別、結構或模組都會在範圍中。  
  
-   **存留期** ：外部參考與宣告它的類別、結構或模組具有相同的存留期 \(Lifetime\)。  
  
-   **呼叫外部程序** 您可以利用與您呼叫 `Function` 或 `Sub` 程序的相同方式呼叫外部程序：如果它會傳回值，則在運算式中使用它；或如果它未傳回值，則在 [Call Statement](../../../visual-basic/language-reference/statements/call-statement.md) 指定它。  
  
     您可以完全按照 `Declare` 陳述式中的 `parameterlist` 所指定，將引數傳遞至外部程序，  不要考慮參數原先如何在外部檔案中宣告。  同樣地，如果有一個傳回值，請完全按照 `Declare` 陳述式中的 `returntype` 所指定來使用它。  
  
-   **字元集** 當 Visual Basic 呼叫外部程序時，您可以在 `charsetmodifier` 中指定 Visual Basic 應該如何封送處理 \(Marshal\) 字串。  `Ansi` 修飾詞 \(Modifier\) 會引導 Visual Basic 將所有字串封送處理為 ANSI 值，而 `Unicode` 修飾詞則會引導它將所有字串封送處理為 Unicode 值。  `Auto` 修飾詞會根據外部參考 `name` 或 `aliasname` \(如果有指定的話\)，引導 Visual Basic 按照 .NET Framework 規則封送處理字串。  預設值是 `Ansi`。  
  
     `charsetmodifier` 也會指定 Visual Basic 應該如何查閱其外部檔案內的外部程序。  `Ansi` 和 `Unicode` 都會指示 Visual Basic 來查詢它，而不在搜尋期間修改它的名稱。  `Auto` 會指示 Visual Basic 判斷執行階段平台的基底字元集，並可能修改外部程序名稱，如下所示：  
  
    -   在 ANSI 平台 \(如 Windows 95、Windows 98 或 Windows Millennium Edition\) 上，在不修改名稱的情況下，先查閱外部程序。  如果失敗的話，請將 "A" 附加到外部程序名稱的尾端，然後再次進行查閱。  
  
    -   在 Unicode 平台 \(如 Windows NT、Windows 2000 或 Windows XP\) 上，在不修改名稱的情況下，先查閱外部程序。  如果失敗的話，請將 "W" 附加到外部程序名稱的尾端，然後再次進行查閱。  
  
-   **機制。** Visual Basic 會使用 .NET Framework「*平台叫用*」\(PInvoke\) 機制解析並存取外部程序。  `Declare` 陳述式和 <xref:System.Runtime.InteropServices.DllImportAttribute> 類別兩者都會自動使用這個機制，因此您不需要了解 PInvoke。  如需詳細資訊，請參閱 [Walkthrough: Calling Windows APIs](../Topic/Walkthrough:%20Calling%20Windows%20APIs%20\(Visual%20Basic\).md)。  
  
> [!IMPORTANT]
>  如果外部程序在 Common Language Runtime \(CLR\) 外執行，它就是「*Unmanaged 程式碼*」。  當您呼叫此種程序時，例如 Win32 API 函式或 COM 方法，您可能會讓應用程式暴露於安全性風險下。  如需詳細資訊，請參閱 [Secure Coding Guidelines for Unmanaged Code](../Topic/Secure%20Coding%20Guidelines%20for%20Unmanaged%20Code.md)。  
  
## 範例  
 下列範例會宣告 `Function` 程序的外部參考，該程序會傳回目前使用者名稱。  接著，它會呼叫外部程序 `GetUserNameA` 做為 `getUser` 的一部分。  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_1.vb)]  
  
## 範例  
 <xref:System.Runtime.InteropServices.DllImportAttribute> 提供了在 Unmanaged 程式碼中使用函式的另一種方式。  下列範例會在不使用 `Declare` 陳述式的情況下宣告匯入函式。  
  
 [!code-vb[VbVbalrStatements#16](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_2.vb)]  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_3.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Call Statement](../../../visual-basic/language-reference/statements/call-statement.md)   
 [Walkthrough: Calling Windows APIs](../Topic/Walkthrough:%20Calling%20Windows%20APIs%20\(Visual%20Basic\).md)