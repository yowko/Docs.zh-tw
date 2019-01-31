---
title: '建立組件資訊清單時發生錯誤: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: f9c8d9fe4b8bea45e4b655415b044937f248deab
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266477"
---
# <a name="error-creating-assembly-manifest-error-message"></a>建立組件資訊清單時發生錯誤：\<錯誤訊息 >
Visual Basic 編譯器呼叫組件連結器 (Al.exe，也稱為 Alink)，以產生資訊清單的組件。 連結器在建立組件的前置發出階段回報了錯誤。  
  
 如果指定的金鑰檔或金鑰容器有問題，便可能發生此情形。 若要完全簽署組件，您必須提供有效的金鑰檔，其中包含公開和私密金鑰的相關資訊。 若要延遲簽署組件，您必須選取 [僅延遲簽署] 核取方塊，並提供有效的金鑰檔，其中包含公開金鑰資訊的相關資訊。 延遲簽署組件時不需要私密金鑰。 如需詳細資訊，請參閱[＜How to：使用強式名稱簽署組件](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。  
  
 **錯誤 ID:** BC30140  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  檢查引用的錯誤訊息，並參考主題[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)。 取得錯誤 AL1019 的進一步說明和建議  
  
2.  如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。  
  
## <a name="see-also"></a>另請參閱
- [如何：使用強式名稱簽署組件](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [專案設計工具、 簽署頁](/visualstudio/ide/reference/signing-page-project-designer)
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)。  
- [告訴我們](/visualstudio/ide/talk-to-us)
