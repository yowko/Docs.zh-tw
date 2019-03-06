---
title: .NET 中的組件
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
---
# <a name="assemblies-in-net"></a>.NET 中的組件

組件會構成 .NET 型應用程式之部署、版本控制、重複使用、啟動範圍和安全性權限的基本單位。 組件會以可執行檔 (.exe) 或動態連結程式庫 (.dll) 檔案的形式呈現，而且是 .NET 應用程式的建置組塊。 它們為通用語言執行平台提供了感知型別實作所需的資訊。 您可以將組件視為型別和資源的集合，其構成功能的邏輯單元，而且是為了共同運作而建置。  
  
 在 .NET Core 及 .NET Framework 中，一個組件可由一或多個原始程式碼檔案建置而成。 在 .NET Framework 中，組件可以包含一或多個模組。 如此便可以透過由個別開發人員處理不同原始程式碼檔案或模組，再將其合併來建立單一組件等方式，來規劃較大型的專案。 如需模組的詳細資訊，請參閱[如何：建置多檔案組件](../../framework/app-domains/how-to-build-a-multifile-assembly.md)主題。
  
 組件包含下列屬性：  
  
-   組件會實作為 .exe 或 .dll 檔。  
  
-   針對以 .NET Framework 為目標的程式庫，您可以藉由將組件放進[全域組件快取](../../framework/app-domains/gac.md)，在應用程式之間共用組件。 組件必須經強式命名後才能包含在全域組件快取內。 如需詳細資訊，請參閱[強式名稱的組件](../../framework/app-domains/strong-named-assemblies.md)。  
  
-   系統只會在需要時才將組件載入到記憶體。 如果不使用，則不會予以載入。 這表示使用組件可以有效地管理大型專案中的資源。  
  
-   藉由使用反映，您能以程式設計方式取得組件的相關資訊。 如需詳細資訊，請參閱[反映 (C#)](../../csharp/programming-guide/concepts/reflection.md) 或 [Reflection (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md) (反映 (Visual Basic))。   
  
-   您可以藉由呼叫方法 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>，來僅為了檢查組件載入該組件。  
  
## <a name="assembly-manifest"></a>資訊清單  
 每個組件內都有「組件資訊清單」。 類似於目錄，組件資訊清單包含下列資訊︰  
  
-   組件的身分識別 (其名稱和版本)。  
  
-   一個檔案表格，描述構成該組件的所有其他檔案，例如由您建立且您 .exe 或 .dll 檔案所依賴的其他組件，甚至是點陣圖或讀我檔案。  
  
-   一個「組件參考清單」，它是所有外部相依性的清單，可能是由他人建立而您應用程式需要的 .dll 或其他檔案。 組件參考同時包含全域和私用物件的參考。 所有其他應用程式皆可使用全域物件。 在 .NET Core 中，它們會與特定的 .NET Core 執行階段結合。 在 .NET Framework 中，它們位於全域組件快取內。 <xref:System.IO?displayProperty=nameWithType> 命名空間就是全域組件快取中組件的一個例子。 私用物件必須同樣位在您的應用程式安裝目錄中或位在其底下的目錄。  
  
 因為組件包含內容、版本設定及相依性的相關資訊，所以使用它們的應用程式不需依賴 Windows 登錄值就能正常運作。 組件可減少 .dll 衝突，並讓您的應用程式更可靠，也更容易部署。 在許多情況下，您只要將 .NET 型應用程式的檔案複製到目標電腦，即完成安裝。 如需詳細資訊，請參閱[資訊清單](../../framework/app-domains/assembly-manifest.md)。  
  
## <a name="adding-a-reference-to-an-assembly"></a>將參考新增至組件  
 若要使用組件，您必須加入對它的參考。 接著，您可以針對 C# 使用 [using 指示詞](../../csharp/language-reference/keywords/using-directive.md)，或針對 Visual Basic 使用 [Imports 陳述式](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)，來選擇您欲使用項目的命名空間。 在參考並匯入組件後，您的應用程式即可使用其所有可存取的類型、屬性、方法及命名空間的其他成員，他們的程式碼就如同您來源檔案的一部分。  
 
> [!NOTE]
> 系統會自動參考 .NET 類別庫中的大多數組件。 然而在某些情況下，有些系統組件不會受到自動參考。 在 .NET Core 中，您可以藉由使用 Visual Studio 中的 NuGet 套件管理員，或將組件的 [<PackageReference>](../../core/tools/dependencies.md#the-new-packagereference-element) 元素新增至 *.csproj 或 *.vbproj 專案中，來將參考新增至包含該組件的 NuGet 套件。 在 .NET Framework 中，您可以藉由使用 Visual Studio 中的 [新增參考] 對話方塊，或使用 [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) 或 [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) 編譯器的 `-reference` 命令列選項，來將參考新增至組件。
 
 在 C# 中，您也可以在單一應用程式中使用同一組件的兩種版本。 如需詳細資訊，請參閱[外部別名](../../csharp/language-reference/keywords/extern-alias.md)。  
  
## <a name="creating-an-assembly"></a>建立組件  
 請藉由在 Visual Studio 中建置應用程式、使用 .NET Core 命令列介面 (CLI) 從命令列建置應用程式，或使用命令列編譯器建置 .NET Framework 組件，來編譯您的應用程式。 如需使用 .NET CLI 工具建置組件的詳細資訊，請參閱 [.NET Core 命令列介面 (CLI) 工具](../../core/tools/index.md)。 如需使用命令列編譯器建置組件的資訊，針對 C# 請參閱[使用 csc.exe 建置命令列](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)，針對 Visual Basic 請參閱[從命令列建置](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。  
  
> [!NOTE]
>  若要在 Visual Studio 中建置組件，請在[建置] 功能表中選擇 [建置]。  

## <a name="see-also"></a>另請參閱

 - [.NET 組件檔格式](file-format.md)
 - [Common Language Runtime 中的組件](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 - [Friend 組件](friend-assemblies.md)  
 - [如何：載入和卸載組件 (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)  
 - [如何：載入和卸載組件 (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)  
 - [如何：在 .NET Core 中使用組件解除載入性及進行偵錯](unloadability-howto.md)
 - [如何：判斷檔案是否為組件 (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)  
 - [如何：判斷檔案是否為組件 (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)  
