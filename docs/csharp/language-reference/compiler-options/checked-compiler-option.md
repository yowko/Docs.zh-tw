---
title: -checked (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 814e8f3aa7130c6a64e7e27951854bed7b7cbe6c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333934"
---
# <a name="-checked-c-compiler-options"></a>-checked (C# 編譯器選項)
**-checked** 選項會指定產生超出該資料類型範圍之值且不在 [checked](../../../csharp/language-reference/keywords/checked.md) 或 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) 關鍵字範圍內的整數算術陳述式是否導致執行階段例外狀況。  
  
## <a name="syntax"></a>語法  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>備註  
 在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式不一定會有 **-checked** 選項的效果。  
  
 如果不在 `checked` 或 `unchecked` 關鍵字範圍內的整數算術陳述式產生超出該資料類型範圍的值，並在編譯時使用 **-checked+** (或 **-checked**)，則該陳述式會在執行階段導致例外狀況。 如果在編譯時使用 **-checked-**，則該陳述式不會在執行階段導致例外狀況。  
  
 這個選項的預設值是 **-checked-**；溢位檢查已停用。
 
 有時候，用來建置大型應用程式的自動化工具會將 -checked 設定為 +。 一種使用 -checked- 的情況是透過指定 -checked- 來覆寫工具的全域預設值。
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1. 開啟專案的 [屬性] 頁面。 如需詳細資訊，請參閱[專案設計工具、建置頁 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)。  
  
2. 按一下 [建置] 屬性頁面。  
  
3. 按一下 [ **進階** ] 按鈕。  
  
4. 修改 [檢查算術溢位/反向溢位] 屬性。  
  
 若要以程式設計方式存取這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>。  
  
## <a name="example"></a>範例  
 下列命令會編譯 `t2.cs`。 在命令中使用 `-checked` 會指定檔案中不在 `checked` 或 `unchecked` 關鍵字範圍內且產生超出該資料型別範圍之值的任何整數算術陳述式，都會在執行階段導致例外狀況。  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
