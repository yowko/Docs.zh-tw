---
title: '無法發出組件: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 404a8255adcdc414a40b40395ada1c90c1078325
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "42754063"
---
# <a name="unable-to-emit-assembly-error-message"></a>無法發出組件：\<錯誤訊息 >

Visual Basic 編譯器呼叫組件連結器 (*Al.exe*，也稱為 Alink) 來產生組件資訊清單和連結器會在建立組件的發出階段回報錯誤。

**錯誤 ID:** BC30145

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 檢查引用的錯誤訊息，並參考主題[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)取得進一步說明和建議。

2. 嘗試簽署組件以手動的方式，使用[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)或[Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)。

3. 如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。

### <a name="to-sign-the-assembly-manually"></a>手動簽署組件

1. 使用  [Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)) 來建立公開/私密金鑰組檔案。

   此檔案具有 *.snk*延伸模組。

2. 從專案刪除產生錯誤的 COM 參考。

3. 開啟[Visual Studio 的開發人員命令提示字元](../../../framework/tools/developer-command-prompt-for-vs.md)。

   在 Windows 10 中，輸入**開發人員命令提示字元**在工作列上的搜尋 方塊。 然後，選取**適用於 VS 2017 開發人員命令提示字元**從結果清單中。

4. 將目錄變更至您要在其中放置您的組件包裝函式的目錄。

5. 輸入下列命令：

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   您可以輸入實際命令的範例是：

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > 如果路徑或檔案包含空格，請使用雙引號。

6. 在 Visual Studio 中，加入.NET 組件參考，您剛剛建立的檔案。

## <a name="see-also"></a>另請參閱

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)。
- [Sn.exe （強式名稱工具）][Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md))
- [如何：建立公開/私密金鑰組](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [告訴我們](/visualstudio/ide/talk-to-us)