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
ms.openlocfilehash: 7ac9ea194095832f6c3825ce414350bca89c26fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107235"
---
# <a name="assemblies-in-net"></a>.NET 中的組件

元件會形成部署、版本控制、重複使用、啟用範圍和安全性許可權的基本單位。以網路為基礎的應用程式。 組件是建置來共同運作及構成一個功能邏輯單位的型別與資源集合。 元件採用可執行檔（ *.exe*）或動態連結程式庫（ *.dll*）檔案的形式，而且是 .net 應用程式的建立區塊。 它們為通用語言執行平台提供了感知型別實作所需的資訊。 您可以將組件視為型別和資源的集合，其構成功能的邏輯單元，而且是為了共同運作而建置。

在 .NET Core 和 .NET Framework 中，您可以從一或多個原始程式碼檔建立元件。 在 .NET Framework 中，組件可以包含一或多個模組。 這可讓您規劃更大的專案，讓數個開發人員可以使用個別的原始程式碼檔案或模組，這些檔案會結合以建立單一元件。 如需模組的詳細資訊，請參閱[如何：建立](../../framework/app-domains/build-multifile-assembly.md)多檔案元件。

組件包含下列屬性：

- 元件會實作為 *.exe*或 *.dll*檔案。

- 針對以 .NET Framework 為目標的程式庫，您可以將元件放在[全域組件快取（GAC）](../../framework/app-domains/gac.md)中，以在應用程式之間共用它們。 您必須先將元件強式名稱，才可以將它們包含在 GAC 中。 如需詳細資訊，請參閱[強式名稱的元件](strong-named.md)。

- 系統只會在需要時才將組件載入到記憶體。 如果未使用，則不會載入它們。 這表示使用組件可以有效地管理大型專案中的資源。

- 藉由使用反映，您能以程式設計方式取得組件的相關資訊。 如需詳細資訊，請參閱[反映 (C#)](../../csharp/programming-guide/concepts/reflection.md) 或 [Reflection (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md) (反映 (Visual Basic))。

- 您可以載入元件，只使用 .NET Core 中的 <xref:System.Reflection.MetadataLoadContext> 類別，以及 .NET Core 和 .NET Framework 中的 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> 或 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> 方法來加以檢查。

## <a name="assemblies-in-the-common-language-runtime"></a>Common language runtime 中的元件

元件會提供通用語言執行平臺所需的資訊，以感知型別實作為。 對於執行階段而言，型別不會存在於組件的內容以外。 

元件會定義下列資訊：  
  
- Common language runtime 所執行的程式碼。 請注意，每個元件只能有一個進入點： `DllMain`、`WinMain` 或 `Main`。
  
- 安全性界限。 組件是要求和授與權限的單位。 如需元件中安全性界限的詳細資訊，請參閱[元件安全性考慮](security-considerations.md)。  
  
- 類型界限。 每種型別的識別都包含該型別所在之組件的名稱。 在某個組件範圍中載入的型別 `MyType` 與在另一個組件範圍中載入的型別 `MyType` 不同。 
  
- 參考範圍界限。 [組件資訊清單](#assembly-manifest)具有用來解析類型及滿足資源要求的中繼資料。 資訊清單會指定要在元件外部公開的類型和資源，並列舉其相依的其他元件。 可移植執行檔（PE）中的 Microsoft 中繼語言（MSIL）程式碼不會執行，除非它有相關聯的[元件資訊清單](#assembly-manifest)。
  
- 版本界限。 元件是 common language runtime 中的最小可控制版本單位。 相同元件中的所有類型和資源都是以一個單位進行版本設定。 [組件資訊清單](#assembly-manifest)會描述您為任何相依元件指定的版本相依性。 如需版本控制的詳細資訊，請參閱[元件版本控制](versioning.md)。  
  
- 部署單位。 當應用程式啟動時，一定要有應用程式一開始所呼叫的組件。 其他元件（例如包含當地語系化資源或公用程式類別的元件）則可依需求抓取。 這可讓應用程式在第一次下載時保持簡單且精簡。 如需部署元件的詳細資訊，請參閱[部署應用程式](../../framework/deployment/index.md)。  
  
- 並存執行單位。 如需有關執行元件之多個版本的詳細資訊，請參閱[元件和並存執行](side-by-side-execution.md)。  

## <a name="create-an-assembly"></a>建立元件

組件可以是靜態，也可以是動態。 靜態組件儲存在磁碟上的可攜式執行檔 (PE) 中。 靜態元件可以包含介面、類別和資源（例如點陣圖、JPEG 檔案和其他資源檔）。 您也可以建立動態元件，它們會直接從記憶體執行，而且不會在執行前儲存至磁片。 您可以在執行動態組件之後，再將其儲存至磁碟。  

您可以使用幾種方式建立組件。 您可以使用可建立 *.dll*或 *.exe*檔案的開發工具（例如 Visual Studio）。 您可以使用 Windows SDK 中的工具，利用其他開發環境中的模組來建立元件。 您也可以使用 Common Language Runtime API (例如 <xref:System.Reflection.Emit?displayProperty=nameWithType>) 來建立動態組件。 

藉由使用 .NET Core 命令列介面工具建立元件，或使用命令列編譯器建立 .NET Framework 元件，藉 Visual Studio 以編譯元件。 如需使用 .NET Core 命令列介面工具來建立元件的詳細資訊，請參閱[.Net core 命令列介面工具](../../core/tools/index.md)。 For building assemblies with the command-line compilers, see [Command-line build with csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) for C#, or [Build from the command line](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) for Visual Basic.

> [!NOTE]
> To build an assembly in Visual Studio, on the **Build** menu, select **Build**.

## <a name="assembly-manifest"></a>資訊清單

Every assembly has an *assembly manifest* file. Similar to a table of contents, the assembly manifest contains:

- 組件的身分識別 (其名稱和版本)。

- A file table describing all the other files that make up the assembly, such as other assemblies you created that your *.exe* or *.dll* file relies on, bitmap files, or Readme files.

- An *assembly reference list*, which is a list of all external dependencies, such as *.dll*s or other files. 組件參考同時包含全域和私用物件的參考。 所有其他應用程式皆可使用全域物件。 In .NET Core, global objects are coupled with a particular .NET Core runtime. In .NET Framework, global objects reside in the global assembly cache (GAC). *System.IO.dll* is an example of an assembly in the GAC. Private objects must be in a directory level at or below the directory in which your app is installed.

Because assemblies contain information about content, versioning, and dependencies, the applications that use them needn't rely on external sources, such as the registry on Windows systems, to function properly. Assemblies reduce *.dll* conflicts and make your applications more reliable and easier to deploy. 在許多情況下，您只要將 .NET 型應用程式的檔案複製到目標電腦，即完成安裝。 For more information, see [Assembly manifest](manifest.md).

## <a name="add-a-reference-to-an-assembly"></a>Add a reference to an assembly

To use an assembly in an application, you must add a reference to it. Once an assembly is referenced, all the accessible types, properties, methods, and other members of its namespaces are available to your application as if their code were part of your source file.

> [!NOTE]
> 系統會自動參考 .NET 類別庫中的大多數組件。 If a system assembly isn't automatically referenced, for .NET Core, you can add a reference to the NuGet package that contains the assembly. Either use the NuGet Package Manager in Visual Studio, or add a [\<PackageReference>](../../core/tools/dependencies.md#the-new-packagereference-element) element for the assembly to the *.csproj* or *.vbproj* project. In .NET Framework, you can add a reference to the assembly by using the **Add Reference** dialog in Visual Studio, or by using the `-reference` command line option for the [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) or [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) compilers.

In C#, you can use two versions of the same assembly in a single application. 如需詳細資訊，請參閱[外部別名](../../csharp/language-reference/keywords/extern-alias.md)。

## <a name="related-content"></a>相關內容
  
|標題|描述|  
|-----------|-----------------|  
|[Assembly contents](contents.md)|Elements that make up an assembly.|  
|[Assembly manifest](manifest.md)|Data in the assembly manifest, and how it is stored in assemblies.|  
|[Global assembly cache](../../framework/app-domains/gac.md)|How the GAC stores and uses assemblies.|  
|[強式名稱的組件](strong-named.md)|Characteristics of strong-named assemblies.|  
|[Assembly security considerations](security-considerations.md)|How security works with assemblies.|  
|[Assembly versioning](versioning.md)|Overview of the .NET Framework versioning policy.|  
|[Assembly placement](../../framework/app-domains/assembly-placement.md)|Where to locate assemblies.|  
|[Assemblies and side-by-side execution](side-by-side-execution.md)|Use multiple versions of the runtime or an assembly simultaneously.|  
|[Program with assemblies](program.md)|How to create, sign, and set attributes on assemblies.|  
|[Emit dynamic methods and assemblies](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|How to create dynamic assemblies.|  
|[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|How the .NET Framework resolves assembly references at run time.|  

## <a name="reference"></a>參考資料  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>請參閱

- [.NET 組件檔格式](file-format.md)
- [.NET 中的組件](index.md)
- [Friend assemblies](friend.md)
- [Reference assemblies](reference-assemblies.md)
- [How to: Load and unload assemblies](load-unload.md)
- [How to: Use and debug assembly unloadability in .NET Core](unloadability.md)
- [How to: Determine if a file is an assembly](identify.md)
