---
title: "無法發出組件：&lt;錯誤訊息&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b19b6439d85822c69adac0b3e0e04b2f31299836
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>無法發出組件：&lt;錯誤訊息&gt;
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器呼叫組件連結器 (Al.exe，也稱為 Alink) 使用資訊清單產生組件，連結器在建立組件的發出階段回報錯誤。  
  
 **錯誤 ID:** BC30145  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查引用的錯誤訊息，請參閱主題[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)。 以取得進一步說明和建議。  
  
2.  再試一次 簽署組件以手動方式，使用[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)或[Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)。  
  
3.  如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。  
  
### <a name="to-sign-the-assembly-manually"></a>手動簽署組件  
  
1.  使用 [Sn.exe （強式名稱工具）][Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)) 建立公開/私密金鑰組檔案。  
  
     這個檔案的副檔名為 .snk。  
  
2.  從專案刪除產生錯誤的 COM 參考。  
  
3.  從 Windows**啟動**功能表上，指向**程式**，指向  **Microsoft Visual Studio 2008**，指向  **Visual Studio Tools**，和然後按一下  **Visual Studio 2008 命令提示字元**。  
  
4.  移到您要放置組件包裝函式的目錄。  
  
5.  輸入下列程式碼。  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     您可能輸入的程式碼範例如下。  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     如果路徑或檔案包含空格，請使用雙引號 (")。  
  
6.  在 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 中，加入您剛建立之檔案的 .NET Assembly 參考。  
  
## <a name="see-also"></a>請參閱  
 
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)。  
 [Sn.exe （強式名稱工具）][Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md))  
 [如何：建立公開/私密金鑰組](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [告訴我們](/visualstudio/ide/talk-to-us)
