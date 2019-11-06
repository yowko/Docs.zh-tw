---
title: '建立組件資訊清單時發生錯誤: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 7ccfb970a0e471b4a7e6808f041dfea2f386e7e9
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197131"
---
# <a name="error-creating-assembly-manifest-error-message"></a>建立組件資訊清單時發生錯誤： \<錯誤訊息 >
Visual Basic 編譯器會呼叫元件連結器（Al.exe，也稱為 Alink），以產生具有資訊清單的元件。 連結器在建立組件的前置發出階段回報了錯誤。  
  
 如果指定的金鑰檔或金鑰容器有問題，便可能發生此情形。 若要完全簽署組件，您必須提供有效的金鑰檔，其中包含公開和私密金鑰的相關資訊。 若要延遲簽署組件，您必須選取 [僅延遲簽署] 核取方塊，並提供有效的金鑰檔，其中包含公開金鑰資訊的相關資訊。 延遲簽署組件時不需要私密金鑰。 如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../standard/assembly/sign-strong-name.md)。  
  
 **錯誤識別碼：** BC30140  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 檢查加上引號的錯誤訊息，並查閱[al.exe](../../../framework/tools/al-exe-assembly-linker.md)的主題。 針對錯誤 AL1019 進一步的說明和建議  
  
2. 如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。  
  
## <a name="see-also"></a>請參閱

- [操作說明：使用強式名稱簽署組件](../../../standard/assembly/sign-strong-name.md)
- [專案設計工具、簽署頁面](/visualstudio/ide/reference/signing-page-project-designer)
- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [告訴我們](/visualstudio/ide/feedback-options)
