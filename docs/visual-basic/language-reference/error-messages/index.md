---
title: "錯誤訊息 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7f5138d430e6737a4a8a47d4a800905dedff660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="error-messages-visual-basic"></a>錯誤訊息 (Visual Basic)
當您撰寫、編譯或執行 Visual Basic 應用程式時，可能發生下列類型的錯誤：  
  
1.  設計階段錯誤，當您在 Visual Studio 中撰寫應用程式時可能發生。  
  
2.  編譯時期錯誤，當您在 Visual Studio 或於命令提示字元中編譯應用程式時可能發生。  
  
3.  執行階段錯誤，當您在 Visual Studio 中執行應用程式，或是以獨立的可執行檔執行應用程式時可能發生。  
  
 如需有關如何針對特定錯誤進行疑難排解的詳細資訊，請參閱[Visual Basic 程式設計人員的其他資源](../../../visual-basic/getting-started/additional-resources.md)。  
  
## <a name="run-time-errors"></a>執行階段錯誤  
 如果 Visual Basic 應用程式嘗試執行系統無法執行的動作，則會發生執行階段錯誤，且 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 會擲回 `Exception` 物件。 透過使用 `Throw` 陳述式，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 可以產生任何資料型別 (包括 `Exception` 物件) 的自訂錯誤。 應用程式可以透過顯示已攔截例外狀況的錯誤碼和訊息來識別錯誤。 如果未攔截到錯誤，應用程式便會結束。  
  
 程式碼可以攔截並檢查執行階段錯誤。 如果您將產生錯誤的程式碼包含在 `Try` 區塊中，您可以攔截相對應 `Catch` 區塊內的所有擲回錯誤。 如需有關如何在程式碼中於執行階段攔截錯誤並加以回應的詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="compile-time-errors"></a>編譯時期錯誤  
 如果 Visual Basic 編譯器遇到程式碼中的問題時，就會發生編譯時期錯誤。 在程式碼編輯器中，您可以輕鬆識別造成錯誤的程式碼行，因為該行程式碼下方會顯示波浪線。 如果您指向該波浪底線或是開啟 [錯誤清單]，將會顯示錯誤訊息 (這也會顯示其他訊息)。  
  
 如果識別碼具有波浪底線，且在最右邊的字元底下顯示短底線，您可以針對類別、建構函式、方法、屬性、欄位或列舉產生虛設常式。 如需詳細資訊，請參閱[使用時產生](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage)。
  
 透過解決 Visual Basic 編譯器的警告，您可能可以撰寫出執行速度較快且具有較少錯誤 (bug) 的程式碼。 這些警告會識別在應用程式執行時可能造成錯誤的程式碼。 例如，如果您嘗試叫用未指派物件變數的成員、在沒有設定傳回值的情況下從函式傳回，或是執行具有邏輯錯誤的 `Try` 區塊以攔截例外狀況，編譯器都會警告您。 如需有關警告的詳細資訊 (包括如何開啟與關閉警告)，請參閱[在 Visual Basic 中設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。
