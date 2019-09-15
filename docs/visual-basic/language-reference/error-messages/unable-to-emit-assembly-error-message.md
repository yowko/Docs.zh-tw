---
title: '無法發出組件: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 530aaee40be92bf72ee4b83b4141108e9b81c8a1
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968859"
---
# <a name="unable-to-emit-assembly-error-message"></a>無法發出元件： \<錯誤訊息 >

Visual Basic 編譯器會呼叫元件連結器（*al.exe*，也稱為 Alink）來產生具有資訊清單的元件，而連結器會在建立元件的發出階段中報告錯誤。

**錯誤識別碼：** BC30145

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 檢查加上引號的錯誤訊息，並查閱[al.exe](../../../framework/tools/al-exe-assembly-linker.md)的主題，以取得進一步的說明和建議。

2. 請嘗試使用[al.exe](../../../framework/tools/al-exe-assembly-linker.md)或[Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)手動簽署元件。

3. 如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。

### <a name="to-sign-the-assembly-manually"></a>手動簽署組件

1. 使用[sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)）來建立公開/私密金鑰組檔案。

   這個檔案的副檔名為 *.snk* 。

2. 從專案刪除產生錯誤的 COM 參考。

3. 開啟 Visual Studio 的 [[開發人員命令提示字元](../../../framework/tools/developer-command-prompt-for-vs.md)]。

   在 Windows 10 的 [搜尋] 方塊中，輸入「**開發人員命令提示**字元」。 然後，從結果清單中選取 [**適用于 VS 2017 的開發人員命令提示字元**]。

4. 將目錄變更為您要放置元件包裝函式的目錄。

5. 輸入下列命令：

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   您可能會輸入的實際命令範例如下：

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > 如果路徑或檔案包含空格，請使用雙引號。

6. 在 Visual Studio 中，將 .NET 元件參考新增至您剛才建立的檔案。

## <a name="see-also"></a>另請參閱

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (強式名稱工具)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [如何：建立公開/私密金鑰組](../../../standard/assembly/create-public-private-key-pair.md)
- [告訴我們](/visualstudio/ide/talk-to-us)
