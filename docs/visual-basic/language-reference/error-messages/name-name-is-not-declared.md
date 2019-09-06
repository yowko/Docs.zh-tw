---
title: 名稱 '<name>' 未宣告
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: dfa1d1600c7943e503b4f5ec2e2b8ecd6fbb9fe0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254193"
---
# <a name="name-name-is-not-declared"></a>名稱 '\<name > ' 未宣告
語句參考了程式設計專案，但編譯器找不到具有該確切名稱的元素。  
  
 **錯誤識別碼：** BC30451  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請檢查參考陳述式中的名稱拼寫。 Visual Basic 不區分大小寫，但拼寫中的任何其他變化都會被視為完全不同的名稱。 請注意，底線 (`_`) 是名稱的一部分，因此也是拼字的一部分。  
  
2. 檢查物件及其成員之間是否有成員存取`.`運算子（）。 例如，如果您有 <xref:System.Windows.Forms.TextBox> 控制項，名為 `TextBox1`，那麼要存取它的 <xref:System.Windows.Forms.TextBoxBase.Text%2A> 屬性，您應該輸入 `TextBox1.Text`。 如果您改為輸入 `TextBox1Text`，便會建立不同的名稱。  
  
3. 如果拼寫正確，且任何物件成員存取的語法都正確，請確認已宣告該元素。 如需詳細資訊，請參閱宣告的[元素](../../programming-guide/language-features/declared-elements/index.md)。  
  
4. 如果已宣告程式設計項目，請檢查它是否在範圍內。 如果參考的語句不在宣告程式設計專案的區域之外，您可能需要限定專案名稱。 如需詳細資訊，請參閱 [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md)。  

5. 如果您不是使用完整型別或型別和成員名稱（例如，您的程式碼將屬性參考為`MethodInfo.Name` ， `System.Reflection.MethodInfo.Name`而不是），請加入[Imports 語句](../statements/imports-statement-net-namespace-and-type.md)。

6. 如果您嘗試編譯 SDK 樣式的專案（vbproj 檔案開頭為行\* `<Project Sdk="Microsoft.NET.Sdk">`的專案），且錯誤訊息參考到類型或成員，則會將您的應用程式設定為使用 Visual Basic 執行時間程式庫的參考進行編譯。 根據預設，程式庫的子集會內嵌在 SDK 樣式專案的元件中。

   例如，下列範例無法編譯，因為<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName>找不到方法。 它不會內嵌在應用程式隨附的 Visual Basic 執行時間子集。  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   若要解決這個錯誤，請`<VBRuntime>Default</VBRuntime>`將專案新增至`<PropertyGroup>` [專案] 區段，如下列 Visual Basic 專案檔所示。

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>另請參閱

- [宣告和常數摘要](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
