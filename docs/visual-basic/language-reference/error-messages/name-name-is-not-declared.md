---
title: 名稱 '<name>' 未宣告
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 3aadc49f91021409123550ba2712f1acf5b99d83
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260123"
---
# <a name="name-name-is-not-declared"></a>名稱 '\<名稱 >' 未宣告
陳述式是指程式設計項目，但編譯器找不到具有相同名稱的項目。  
  
 **錯誤 ID:** BC30451  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請檢查參考陳述式中的名稱拼寫。 Visual Basic 是不區分大小寫，但拼字的任何其他變化會視為完全不同的名稱。 請注意，底線 (`_`) 是名稱的一部分，因此也是拼字的一部分。  
  
2. 請檢查您是否具有成員存取運算子 (`.`) 之間的物件和其成員。 例如，如果您有 <xref:System.Windows.Forms.TextBox> 控制項，名為 `TextBox1`，那麼要存取它的 <xref:System.Windows.Forms.TextBoxBase.Text%2A> 屬性，您應該輸入 `TextBox1.Text`。 如果您改為輸入 `TextBox1Text`，便會建立不同的名稱。  
  
3. 如果拼字正確，且正確的任何物件的成員存取語法，請確認已宣告的項目。 如需詳細資訊，請參閱 < [Declared Elements](../../programming-guide/language-features/declared-elements/index.md)。  
  
4. 如果宣告的程式設計項目，檢查它是否在範圍內。 如果參考陳述式是區域宣告的程式設計項目之外，您可能需要限定項目名稱。 如需詳細資訊，請參閱 [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md)。  

5. 如果您未使用的完整型別或型別和成員的名稱 (例如，您的程式碼指的是做為屬性`MethodInfo.Name`而非`System.Reflection.MethodInfo.Name`)，新增[Imports 陳述式](../statements/imports-statement-net-namespace-and-type.md)。

6. 如果您嘗試編譯 SDK 樣式專案 (專案\*.vbproj 檔案開頭的行`<Project Sdk="Microsoft.NET.Sdk">`)，並出現錯誤訊息是指型別或成員 Microsoft.VisualBasic.dll 組件中的，設定您的應用程式編譯 Visual Basic 執行階段程式庫的參考。 根據預設，程式庫的子集會內嵌在您的組件中的 SDK 樣式專案。

   例如，下列範例無法編譯，因為<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName>找不到方法。 它不會內嵌在 Visual Basic 執行階段隨附於您的應用程式的子集。  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb)]

   若要解決這個錯誤，新增`<VBRuntime>Default</VBRuntime>`專案項目`<PropertyGroup>`區段中的，如下列 Visual Basic 專案檔所示。

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>另請參閱

- [宣告和常數摘要](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
