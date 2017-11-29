---
title: "組件和全域組件快取 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a53a153851973c735a430056520b01c27b1ef59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a>組件和全域組件快取 (Visual Basic)
組件會構成 .NET 型應用程式之部署、版本控制、重複使用、啟動範圍和安全性權限的基本單位。 組件會採用可執行檔 (.exe) 或動態連結程式庫 (.dll) 的格式，而且是 .NET Framework 的建置組塊。 它們為通用語言執行平台提供了感知型別實作所需的資訊。 您可以將組件視為型別和資源的集合，其構成功能的邏輯單元，而且是為了共同運作而建置。  
  
 組件可以包含一或多個模組。 例如，大型專案的規劃方式可能是讓數個開發人員各自處理個別的模組，然後再全部組成單一組件。 如需模組的詳細資訊，請參閱[如何：建置多檔案組件](https://msdn.microsoft.com/library/226t7yxe)主題。  
  
 組件包含下列屬性：  
  
-   組件會實作為 .exe 或 .dll 檔。  
  
-   您可以將組件放在全域組件快取中，以在應用程式之間共用。 組件必須經強式命名後才能包含在全域組件快取內。 如需詳細資訊，請參閱[強式名稱的組件](https://msdn.microsoft.com/library/wd40t7ad)。  
  
-   系統只會在需要時才將組件載入到記憶體。 如果不使用，則不會予以載入。 這表示使用組件可以有效地管理大型專案中的資源。  
  
-   藉由使用反映，您能以程式設計方式取得組件的相關資訊。 如需詳細資訊，請參閱[反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)。  
  
-   如果載入組件為僅供檢查之用，請使用像是 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 的方法。  
  
## <a name="assembly-manifest"></a>組件資訊清單  
 每個組件內都有「組件資訊清單」。 類似於目錄，組件資訊清單包含下列資訊︰  
  
-   組件的身分識別 (其名稱和版本)。  
  
-   一個檔案表格，說明構成該組件的所有其他檔案，例如，您所建立為 .exe 或 .dll 檔依賴的任何其他組件，甚至是點陣圖或讀我檔案。  
  
-   一個「組件參考清單」，它是所有外部相依性的清單 - 應用程式所需的 .dll 檔或其他檔案，可能是由其他人所建立。 組件參考同時包含全域和私用物件的參考。 全域物件位於全域組件快取中，此區域可供其他應用程式使用，有點像是 System32 目錄。 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 命名空間就是全域組件快取中組件的一個例子。 私用物件必須同樣位在您的應用程式安裝目錄中或位在其底下的目錄。  
  
 因為組件包含有關內容、版本管理及相依性的資訊，所以您使用 Visual Basic 建立的應用程式不依賴 Windows 登錄值就能正常運作。 組件可減少 .dll 衝突，並讓您的應用程式更可靠，也更容易部署。 在許多情況下，您只要將 .NET 型應用程式的檔案複製到目標電腦，即完成安裝。  
  
 如需詳細資訊，請參閱[組件資訊清單](https://msdn.microsoft.com/library/1w45z383)。  
  
## <a name="adding-a-reference-to-an-assembly"></a>加入組件的參考  
 若要使用組件，您必須加入對它的參考。 接著，您要使用 [Imports 陳述式](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)來選擇您想要使用之項目的命名空間。 在參考並匯入組件之後，您的應用程式即可使用所有可存取的類別、屬性、方法及其命名空間的其他成員，其程式碼就如同您原始程式檔的一部分。  
  
## <a name="creating-an-assembly"></a>建立組件  
 使用命令列編譯器從命令列建置來編譯您的應用程式。 如需有關從命令列建置組件的詳細資訊，請參閱[從命令列建置](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。  
  
> [!NOTE]
>  若要在 Visual Studio 中建置組件，請在[建置] 功能表中選擇 [建置]。  
  
## <a name="see-also"></a>另請參閱  
 [Common Language Runtime 中的組件](https://msdn.microsoft.com/library/k3677y81)  
 [Friend 組件 (Visual Basic)](friend-assemblies.md)  
 [如何： 共用組件與其他應用程式 (Visual Basic)](how-to-share-an-assembly-with-other-applications.md)  
 [如何： 載入和卸載組件 (Visual Basic)](how-to-load-and-unload-assemblies.md)  
 [如何： 判斷檔案是否為組件 (Visual Basic)](how-to-determine-if-a-file-is-an-assembly.md)  
 [如何： 建立和使用組件使用命令列 (Visual Basic)](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [逐步解說： 在 Visual Studio (Visual Basic) 中內嵌 Managed 組件的類型](walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [逐步解說：在 Visual Studio 中內嵌來自 Microsoft Office 組件的型別資訊 (Visual Basic)](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
