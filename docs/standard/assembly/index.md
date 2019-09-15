---
title: .NET 中的組件
ms.date: 08/15/2019
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 903a553b5383620f15cce274c61a440b7bbb1d7d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970019"
---
# <a name="assemblies-in-net"></a>.NET 中的組件

元件會形成部署、版本控制、重複使用、啟用範圍和安全性許可權的基本單位。以網路為基礎的應用程式。 組件是建置來共同運作及構成一個功能邏輯單位的型別與資源集合。 元件採用可執行檔（ *.exe*）或動態連結程式庫（ *.dll*）檔案的形式，而且是 .net 應用程式的建立區塊。 它們為通用語言執行平台提供了感知型別實作所需的資訊。 您可以將組件視為型別和資源的集合，其構成功能的邏輯單元，而且是為了共同運作而建置。

在 .NET Core 和 .NET Framework 中，您可以從一或多個原始程式碼檔建立元件。 在 .NET Framework 中，組件可以包含一或多個模組。 這可讓您規劃更大的專案，讓數個開發人員可以使用個別的原始程式碼檔案或模組，這些檔案會結合以建立單一元件。 如需模組的詳細資訊，請參閱[如何：建立多檔案元件](../../framework/app-domains/build-multifile-assembly.md)。

組件包含下列屬性：

- 元件會實作為 *.exe*或 *.dll*檔案。

- 針對以 .NET Framework 為目標的程式庫，您可以將元件放在[全域組件快取（GAC）](../../framework/app-domains/gac.md)中，以在應用程式之間共用它們。 您必須先將元件強式名稱，才可以將它們包含在 GAC 中。 如需詳細資訊，請參閱[強式名稱的元件](strong-named.md)。

- 系統只會在需要時才將組件載入到記憶體。 如果未使用，則不會載入它們。 這表示使用組件可以有效地管理大型專案中的資源。

- 藉由使用反映，您能以程式設計方式取得組件的相關資訊。 如需詳細資訊，請參閱[反映 (C#)](../../csharp/programming-guide/concepts/reflection.md) 或 [Reflection (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md) (反映 (Visual Basic))。

- 您可以載入元件，只要使用 .net core 中的<xref:System.Reflection.MetadataLoadContext>類別，以及 .net core 和 .NET Framework 中的<xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType>或<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>方法，即可加以檢查。

## <a name="assemblies-in-the-common-language-runtime"></a>Common language runtime 中的元件

元件會提供通用語言執行平臺所需的資訊，以感知型別實作為。 對於執行階段而言，型別不會存在於組件的內容以外。 

元件會定義下列資訊：  
  
- Common language runtime 所執行的程式碼。 請注意，每個元件只能有一個進入點`DllMain`： `WinMain`、或`Main`。
  
- 安全性界限。 組件是要求和授與權限的單位。 如需元件中安全性界限的詳細資訊，請參閱[元件安全性考慮](security-considerations.md)。  
  
- 類型界限。 每種型別的識別都包含該型別所在之組件的名稱。 在某個組件範圍中載入的型別 `MyType` 與在另一個組件範圍中載入的型別 `MyType` 不同。 
  
- 參考範圍界限。 [組件資訊清單](#assembly-manifest)具有用來解析類型及滿足資源要求的中繼資料。 資訊清單會指定要在元件外部公開的類型和資源，並列舉其相依的其他元件。 可移植執行檔（PE）中的 Microsoft 中繼語言（MSIL）程式碼不會執行，除非它有相關聯的[元件資訊清單](#assembly-manifest)。
  
- 版本界限。 元件是 common language runtime 中的最小可控制版本單位。 相同元件中的所有類型和資源都是以一個單位進行版本設定。 [組件資訊清單](#assembly-manifest)會描述您為任何相依元件指定的版本相依性。 如需版本控制的詳細資訊，請參閱[元件版本控制](versioning.md)。  
  
- 部署單位。 當應用程式啟動時，一定要有應用程式一開始所呼叫的組件。 其他元件（例如包含當地語系化資源或公用程式類別的元件）則可依需求抓取。 這可讓應用程式在第一次下載時保持簡單且精簡。 如需部署元件的詳細資訊，請參閱[部署應用程式](../../framework/deployment/index.md)。  
  
- 並存執行單位。 如需有關執行元件之多個版本的詳細資訊，請參閱[元件和並存執行](side-by-side-execution.md)。  

## <a name="create-an-assembly"></a>建立元件

組件可以是靜態，也可以是動態。 靜態組件儲存在磁碟上的可攜式執行檔 (PE) 中。 靜態元件可以包含介面、類別和資源（例如點陣圖、JPEG 檔案和其他資源檔）。 您也可以建立動態元件，它們會直接從記憶體執行，而且不會在執行前儲存至磁片。 您可以在執行動態組件之後，再將其儲存至磁碟。  

您可以使用幾種方式建立組件。 您可以使用可建立 *.dll*或 *.exe*檔案的開發工具（例如 Visual Studio）。 您可以使用 Windows SDK 中的工具，利用其他開發環境中的模組來建立元件。 您也可以使用 Common Language Runtime API (例如 <xref:System.Reflection.Emit?displayProperty=nameWithType>) 來建立動態組件。 

藉由使用 .NET Core 命令列介面工具建立元件，或使用命令列編譯器建立 .NET Framework 元件，藉 Visual Studio 以編譯元件。 如需使用 .NET Core 命令列介面工具來建立元件的詳細資訊，請參閱[.Net core 命令列介面工具](../../core/tools/index.md)。 如需使用命令列編譯器來建立元件，請參閱的[命令列組建，其](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)適用于C#的 csc，或[從命令列建立](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)以進行 Visual Basic。

> [!NOTE]
> 若要在 Visual Studio 中建立元件，請在 [**建立**] 功能表上，選取 [**建立**]。

## <a name="assembly-manifest"></a>資訊清單

每個元件都有一個*組件資訊清單*檔。 類似于目錄，組件資訊清單包含：

- 組件的身分識別 (其名稱和版本)。

- 一個檔案表格，描述組成元件的所有其他檔案，例如您所建立的其他元件，亦即您的 *.exe*或 *.dll*檔案依賴、點陣圖檔案或讀我檔案。

- *元件參考清單*，這是所有外部相依性的清單，例如 *.dll*s 或其他檔案。 組件參考同時包含全域和私用物件的參考。 所有其他應用程式皆可使用全域物件。 在 .NET Core 中，全域物件會與特定的 .NET Core 執行時間結合。 在 .NET Framework 中，全域物件位於全域組件快取（GAC）中。 *System.web*是 GAC 中元件的範例。 私用物件必須在您應用程式安裝所在目錄的目錄層級中。

因為元件包含內容、版本設定及相依性的相關資訊，所以使用它們的應用程式不需要依賴外部來源（例如 Windows 系統上的登錄），就能正常運作。 元件可減少 *.dll 的*衝突，讓您的應用程式更可靠且更容易部署。 在許多情況下，您只要將 .NET 型應用程式的檔案複製到目標電腦，即完成安裝。 如需詳細資訊，請參閱[組件資訊清單](manifest.md)。

## <a name="add-a-reference-to-an-assembly"></a>加入元件的參考

若要在應用程式中使用元件，您必須加入它的參考。 參考元件之後，所有可存取的類型、屬性、方法和其命名空間的其他成員，都可供您的應用程式使用，就像其程式碼屬於您的來源檔案。

> [!NOTE]
> 系統會自動參考 .NET 類別庫中的大多數組件。 如果未自動參考系統元件，則針對 .NET Core，您可以加入包含元件之 NuGet 套件的參考。 請使用 Visual Studio 中的 NuGet 套件管理員，或將元件的[ \<PackageReference >](../../core/tools/dependencies.md#the-new-packagereference-element)元素新增至 *.csproj*或 *. vbproj*專案。 在 .NET Framework 中，您可以使用 Visual Studio 中的 [**加入參考**] 對話方塊，或使用`-reference` [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md)或[Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md)編譯器的命令列選項，將參考加入至元件。

在C#中，您可以在單一應用程式中使用相同元件的兩個版本。 如需詳細資訊，請參閱[外部別名](../../csharp/language-reference/keywords/extern-alias.md)。

## <a name="related-content"></a>相關內容
  
|標題|描述|  
|-----------|-----------------|  
|[元件內容](contents.md)|組成元件的元素。|  
|[組件資訊清單](manifest.md)|組件資訊清單中的資料，以及它如何儲存在元件中。|  
|[全域組件快取](../../framework/app-domains/gac.md)|GAC 儲存和使用元件的方式。|  
|[強式名稱的組件](strong-named.md)|強式名稱元件的特性。|  
|[元件安全性考慮](security-considerations.md)|元件的安全性運作方式。|  
|[元件版本控制](versioning.md)|.NET Framework 版本控制原則的總覽。|  
|[元件位置](../../framework/app-domains/assembly-placement.md)|哪裡可以找到元件。|  
|[元件和並存執行](side-by-side-execution.md)|同時使用多個版本的執行時間或元件。|  
|[具有元件的程式](program.md)|如何建立、簽署和設定元件上的屬性。|  
|[發出動態方法和元件](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|如何建立動態元件。|  
|[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|.NET Framework 如何在執行時間解析元件參考。|  

## <a name="reference"></a>參考資料  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>另請參閱

- [.NET 組件檔格式](file-format.md)
- [.NET 中的組件](index.md)
- [Friend 元件](friend.md)
- [如何：載入和卸載元件](load-unload.md)
- [如何：在 .NET Core 中使用和 debug assembly 卸載功能](unloadability.md)
- [如何：判斷檔案是否為元件](identify.md)
