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
ms.openlocfilehash: b61d079a86bdd4a809d44ad128f19a7b358c8384
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228670"
---
# <a name="assemblies-in-net"></a>.NET 中的組件

程式集構成 部署、版本控制、重用、啟動範圍和 的安全許可權的基本單位。基於 NET 的應用程式。 組件是建置來共同運作及構成一個功能邏輯單位的型別與資源集合。 程式集採用可執行 （*.exe*） 或動態連結程式庫 （*.dll*） 檔的形式， 是 .NET 應用程式的構建基塊. 它們為通用語言執行平台提供了感知型別實作所需的資訊。

在 .NET Core 和 .NET 框架中，可以從一個或多個原始程式碼檔構建程式集。 在 .NET Framework 中，組件可以包含一或多個模組。 這允許規劃更大的專案，以便多個開發人員可以處理單獨的原始程式碼檔或模組，這些檔或模組組合起來以創建單個程式集。 有關模組的詳細資訊，請參閱[如何：構建多檔程式集](../../framework/app-domains/build-multifile-assembly.md)。

組件包含下列屬性：

- 程式集作為 *.exe*或 *.dll*檔實現。

- 對於以 .NET 框架為目標的庫，可以通過將程式集放在[全域組件快取 （GAC）](../../framework/app-domains/gac.md)中來在應用程式之間共用組件。 必須先強式名稱程式集，然後才能將它們包含在 GAC 中。 有關詳細資訊，請參閱[強命名程式集](strong-named.md)。

- 系統只會在需要時才將組件載入到記憶體。 如果未使用它們，則未載入它們。 這表示使用組件可以有效地管理大型專案中的資源。

- 藉由使用反映，您能以程式設計方式取得組件的相關資訊。 如需詳細資訊，請參閱[反映 (C#)](../../csharp/programming-guide/concepts/reflection.md) 或 [Reflection (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md) (反映 (Visual Basic))。

- 只需使用 .NET Core 中的<xref:System.Reflection.MetadataLoadContext>類和 .NET Core 和<xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType>.NET 框架中的 or<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>方法，即可載入程式集以對其進行檢查。

## <a name="assemblies-in-the-common-language-runtime"></a>通用語言運行時中的程式集

程式集為通用語言運行時提供需要瞭解類型實現的資訊。 對於執行階段而言，型別不會存在於組件的內容以外。

程式集定義以下資訊：

- 公共語言運行時執行的代碼。 請注意，每個程式集只能有一個進入點： `DllMain` `WinMain`、`Main`或 。

- 安全邊界。 組件是要求和授與權限的單位。 有關程式集中的安全邊界的詳細資訊，請參閱[程式集安全注意事項](security-considerations.md)。

- 類型邊界。 每種型別的識別都包含該型別所在之組件的名稱。 在某個組件範圍中載入的型別 `MyType` 與在另一個組件範圍中載入的型別 `MyType` 不同。

- 引用範圍邊界。 [組件資訊清單](#assembly-manifest)具有用於解析類型和滿足資源請求的中繼資料。 清單指定要在程式集外部公開的類型和資源，並枚舉它所依賴的其他程式集。 微軟中間語言 （MSIL） 代碼在可移植可執行 （PE） 檔中將不會執行，除非它有一個關聯的[組件資訊清單](#assembly-manifest)。

- 版本邊界。 程式集是通用語言運行時中最小的可版本單元。 同一程式集中的所有類型和資源都作為一個單元進行版本控制。 [組件資訊清單](#assembly-manifest)描述為任何依存性程式集指定的版本依賴項。 有關版本控制的詳細資訊，請參閱[程式集版本控制](versioning.md)。

- 部署單元。 當應用程式啟動時，一定要有應用程式一開始所呼叫的組件。 可以按需檢索其他程式集，如包含當地語系化資源或實用程式類的程式集。 這允許應用程式在首次下載時簡單而精簡。 有關部署程式集的詳細資訊，請參閱[部署應用程式](../../framework/deployment/index.md)。

- 並排執行單元。 有關運行程式集的多個版本的詳細資訊，請參閱[程式集和並存執行](side-by-side-execution.md)。

## <a name="create-an-assembly"></a>創建程式集

組件可以是靜態，也可以是動態。 靜態組件儲存在磁碟上的可攜式執行檔 (PE) 中。 靜態程式集可以包括介面、類和資源，如點陣圖、JPEG 檔和其他資源檔。 您還可以創建動態程式集，這些程式集直接從記憶體運行，在執行之前不會保存到磁片。 您可以在執行動態組件之後，再將其儲存至磁碟。

您可以使用幾種方式建立組件。 您可以使用開發工具（如 Visual Studio）來創建 *.dll*或 *.exe*檔。 您可以使用 Windows SDK 中的工具創建包含來自其他開發環境的模組的程式集。 您也可以使用 Common Language Runtime API (例如 <xref:System.Reflection.Emit?displayProperty=nameWithType>) 來建立動態組件。

通過在 Visual Studio 中構建程式集、使用 .NET Core 命令列介面工具構建程式集或使用命令列編譯器構建 .NET 框架程式集來編譯器集。 有關使用 .NET 核心 CLI 構建程式集的詳細資訊，請參閱[.NET 核心 CLI 概述](../../core/tools/index.md)。 有關使用命令列編譯器構建程式集，請參閱 C#[使用 csc.exe 構建命令列，](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或從 Visual Basic[的命令列生成](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。

> [!NOTE]
> 要在 Visual Studio 中構建程式集，請在 **"生成"** 功能表上，選擇 **"生成**"。

## <a name="assembly-manifest"></a>資訊清單

每個程式集都有一個*組件資訊清單*檔。 與目錄類似，組件資訊清單包含：

- 組件的身分識別 (其名稱和版本)。

- 描述構成程式集的所有其他檔的檔表，例如您創建的其他程式集，您的 *.exe*或 *.dll*檔依賴于這些程式集、點陣圖檔或 Readme 檔。

- *程式集引用清單*，它是所有外部依賴項（如 *.dll*s 或其他檔）的清單。 組件參考同時包含全域和私用物件的參考。 所有其他應用程式皆可使用全域物件。 在 .NET Core 中，全域物件與特定的 .NET Core 運行時耦合。 在 .NET 框架中，全域物件駐留在全域組件快取 （GAC）。 *System.IO.dll*是 GAC 中程式集的示例。 私有物件必須位於安裝應用的目錄或下方的目錄級別。

由於程式集包含有關內容、版本控制和保護項的資訊，因此使用它們的應用程式不必依賴外部源（如 Windows 系統上的註冊表）來正常運行。 程式集可減少 *.dll*衝突，並使應用程式更可靠且更易於部署。 在許多情況下，您只要將 .NET 型應用程式的檔案複製到目標電腦，即完成安裝。 有關詳細資訊，請參閱[組件資訊清單](manifest.md)。

## <a name="add-a-reference-to-an-assembly"></a>添加對程式集的引用

要在應用程式中使用程式集，必須添加對程式集的引用。 引用程式集後，應用程式可以使用其命名空間的所有可訪問類型、屬性、方法和其他成員，就像其代碼是原始檔案的一部分一樣。

> [!NOTE]
> 系統會自動參考 .NET 類別庫中的大多數組件。 如果未自動引用系統程式集，對於 .NET Core，則可以添加對包含程式集的 NuGet 包的引用。 在 Visual Studio 中使用 NuGet 包管理器，或者將程式集的[\<包參考>](../../core/tools/dependencies.md#the-packagereference-element)元素添加到 *.csproj*或 *.vbproj*專案中。 在 .NET 框架中，可以使用 Visual Studio 中的 **"增加參考"** 對話方塊或使用[C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md)或`-reference`Visual [Basic](../../visual-basic/reference/command-line-compiler/reference.md)編譯器的命令列選項來添加對程式集的引用。

在 C# 中，您可以在單個應用程式中使用同一程式集的兩個版本。 如需詳細資訊，請參閱[外部別名](../../csharp/language-reference/keywords/extern-alias.md)。

## <a name="related-content"></a>相關內容

|Title|描述|
|-----------|-----------------|
|[組件內容](contents.md)|組成程式集的元素。|
|[組件資訊清單](manifest.md)|組件資訊清單中的資料，以及如何在程式集中存儲資料。|
|[全域組件快取](../../framework/app-domains/gac.md)|GAC 如何存儲和使用程式集。|
|[強命名程式集](strong-named.md)|強命名程式集的特徵。|
|[組件安全性考量](security-considerations.md)|安全性如何與程式集配合使用。|
|[組件版本控制](versioning.md)|.NET 框架版本控制策略的概述。|
|[組件放置](../../framework/app-domains/assembly-placement.md)|位置可定位程式集。|
|[組件和並存執行](side-by-side-execution.md)|同時使用多個版本的運行時或程式集。|
|[發出動態方法和組件](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|如何創建動態程式集。|
|[運行時如何定位程式集](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|.NET 框架如何在運行時解析程式集引用。|

## <a name="reference"></a>參考資料

<xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>另請參閱

- [.NET 組件檔格式](file-format.md)
- [好友程式集](friend.md)
- [參考組件](reference-assemblies.md)
- [如何：載入和卸載程式集](load-unload.md)
- [如何：在 .NET Core 中使用和偵錯工具集卸載](unloadability.md)
- [如何：確定檔是否為程式集](identify.md)
- [如何：使用中繼資料載入上下文檢查程式集內容](inspect-contents-using-metadataloadcontext.md)
