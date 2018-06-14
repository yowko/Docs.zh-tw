---
title: 組件和全域組件快取 (C#)
ms.date: 07/20/2015
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
ms.openlocfilehash: 994498525aed3ebb08f2de7926c7adc2d3d95f56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320921"
---
# <a name="assemblies-and-the-global-assembly-cache-c"></a>組件和全域組件快取 (C#)
組件會構成 .NET 型應用程式之部署、版本控制、重複使用、啟動範圍和安全性權限的基本單位。 組件會採用可執行檔 (.exe) 或動態連結程式庫 (.dll) 的格式，而且是 .NET Framework 的建置組塊。 它們為通用語言執行平台提供了感知型別實作所需的資訊。 您可以將組件視為型別和資源的集合，其構成功能的邏輯單元，而且是為了共同運作而建置。  
  
 組件可以包含一或多個模組。 例如，大型專案的規劃方式可能是讓數個開發人員各自處理個別的模組，然後再全部組成單一組件。 如需模組的詳細資訊，請參閱[如何：建置多檔案組件](../../../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)主題。  
  
 組件包含下列屬性：  
  
-   組件會實作為 .exe 或 .dll 檔。  
  
-   您可以將組件放在全域組件快取中，以在應用程式之間共用。 組件必須經強式命名後才能包含在全域組件快取內。 如需詳細資訊，請參閱[強式名稱的組件](../../../../../docs/framework/app-domains/strong-named-assemblies.md)。  
  
-   系統只會在需要時才將組件載入到記憶體。 如果不使用，則不會予以載入。 這表示使用組件可以有效地管理大型專案中的資源。  
  
-   藉由使用反映，您能以程式設計方式取得組件的相關資訊。 如需詳細資訊，請參閱[反映 (C#)](../../../../csharp/programming-guide/concepts/reflection.md)。  
  
-   如果載入組件是僅供檢查之用，請使用像是 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 的方法。  
  
## <a name="assembly-manifest"></a>組件資訊清單  
 每個組件內都有「組件資訊清單」。 類似於目錄，組件資訊清單包含下列資訊︰  
  
-   組件的身分識別 (其名稱和版本)。  
  
-   一個檔案表格，說明構成該組件的所有其他檔案，例如，您所建立為 .exe 或 .dll 檔依賴的任何其他組件，甚至是點陣圖或讀我檔案。  
  
-   一個「組件參考清單」，它是所有外部相依性的清單 - 應用程式所需的 .dll 檔或其他檔案，可能是由其他人所建立。 組件參考同時包含全域和私用物件的參考。 全域物件位於全域組件快取中，此區域可供其他應用程式使用。 私用物件必須同樣位在您的應用程式安裝目錄中或位在其底下的目錄。  
  
 因為組件包含內容、版本設定及相依性的相關資訊，所以您使用 C# 建立的應用程式不依賴 Windows 登錄值就能正常運作。 組件可減少 .dll 衝突，並讓您的應用程式更可靠，也更容易部署。 在許多情況下，您只要將 .NET 型應用程式的檔案複製到目標電腦，即完成安裝。  
  
 如需詳細資訊，請參閱[組件資訊清單](../../../../../docs/framework/app-domains/assembly-manifest.md)。  
  
## <a name="adding-a-reference-to-an-assembly"></a>加入組件的參考  
 若要使用組件，您必須加入對它的參考。 接著，您要使用 [using 指示詞](../../../../csharp/language-reference/keywords/using-directive.md)來選擇您想要使用之項目的命名空間。 在參考並匯入組件之後，您的應用程式即可使用所有可存取的類別、屬性、方法及其命名空間的其他成員，其程式碼就如同您原始程式檔的一部分。  
  
 在 C# 中，您也可以在單一應用程式中使用同一組件的兩種版本。 如需詳細資訊，請參閱[外部別名](../../../../csharp/language-reference/keywords/extern-alias.md)。  
  
## <a name="creating-an-assembly"></a>建立組件  
 若要編譯您的應用程式，請在 [建置] 功能表上按一下 [建置]，或使用命令列編譯器從命令列建置。 如需從命令列建置組件的詳細資料，請參閱[使用 csc.exe 建置命令列](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  
  
> [!NOTE]
>  若要在 Visual Studio 中建置組件，請在[建置] 功能表中選擇 [建置]。  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../../csharp/programming-guide/index.md)  
 [Common Language Runtime 中的組件](../../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Friend 組件 (C#)](friend-assemblies.md)  
 [如何：與其他應用程式共用組件 (C#)](how-to-share-an-assembly-with-other-applications.md)  
 [如何：載入和卸載組件 (C#)](how-to-load-and-unload-assemblies.md)  
 [如何：判斷檔案是否為組件 (C#)](how-to-determine-if-a-file-is-an-assembly.md)  
 [如何：使用命令列建立和使用組件 (C#)](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [逐步解說：在 Visual Studio 中內嵌來自 Managed 組件的類型 (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [逐步解說：在 Visual Studio 中內嵌來自 Microsoft Office 組件的類型資訊 (C#)](walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
