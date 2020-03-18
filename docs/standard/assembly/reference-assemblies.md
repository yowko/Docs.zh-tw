---
title: 參考組件
description: 瞭解引用程式集，這是 .NET 中一種僅包含庫公共 API 曲面的特殊類型的程式集
author: MSDN-WhiteKnight
ms.date: 09/12/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 938942caf81c54a8aa9207dbe87559438ffb252e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79141064"
---
# <a name="reference-assemblies"></a>參考組件

*引用程式集*是一種特殊類型的程式集，僅包含表示庫的公共 API 曲面所需的最小中繼資料量。 它們包括在生成工具中引用程式集時具有重大意義的所有成員的聲明，但不包括對其 API 協定沒有可觀察到影響的所有成員的實現和聲明。 相反，常規程式集稱為*實現程式集*。

無法載入引用程式集以執行，但它們可以以與實現程式集相同的方式作為編譯器輸入傳遞。 參考程式集通常與特定平臺或庫的軟體發展工具組 （SDK） 一起分發。

使用引用程式集使開發人員能夠構建針對特定庫版本的程式，而無需為該版本提供完整的實現程式集。 假設電腦上只有某些庫的最新版本，但您希望構建針對該庫的早期版本的程式。 如果直接針對實現程式集進行編譯，則可能會無意中使用早期版本中不可用的 API 成員。 只有在目的電腦上測試程式時，您才會發現此錯誤。 如果針對早期版本的引用程式集進行編譯，則將立即收到編譯時間錯誤。

引用程式集還可以表示協定，即一組與具體實現程式集不對應的 API。 此類引用程式集稱為*協定程式集*，可用於定位支援同一組 API 的多個平臺。 例如，.NET 標準提供合同程式集*netstandard.dll*，表示不同 .NET 平臺之間共用的一組公共 API。 這些 API 的實現包含在不同平臺上的不同程式集中，例如 .NET 框架或系統上的 mscorlib.dll.private.CoreLib.dll. *mscorlib.dll* *System.Private.CoreLib.dll* 面向 .NET 標準庫的庫可以在支援 .NET 標準的所有平臺上運行。

## <a name="using-reference-assemblies"></a>使用參考程式集

要使用專案中的某些 API，必須添加對其程式集的引用。 您可以添加對實現程式集或引用程式集的引用。 建議您在可用時使用參考程式集。 這樣做可確保僅使用目標版本中受支援的 API 成員，該成員供 API 設計人員使用。 使用引用程式集可確保不會依賴于實現詳細資訊。

.NET 框架庫的引用程式集與目標包一起分發。 您可以通過下載獨立安裝程式或在 Visual Studio 安裝程式中選擇元件來獲取它們。 有關詳細資訊，請參閱[為開發人員安裝 .NET 框架](../../framework/install/guide-for-developers.md)。 對於 .NET 核心和 .NET 標準，參考程式集根據需要自動下載（通過 NuGet）並引用。 對於 .NET Core 3.0 及更高版本，核心框架的引用程式集位於[Microsoft.NETCore.App.Ref](https://www.nuget.org/packages/Microsoft.NETCore.App.Ref)包中[（Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App)包用於 3.0 之前的版本）。 有關詳細資訊，請參閱 .NET 核心指南中的[包、元包和框架](../../core/packages.md)。

使用"增加參考"對話方塊在 Visual Studio 中添加對 .NET 框架程式集**的引用**時，將從清單中選擇一個程式集，Visual Studio 會自動查找與專案中選擇的目標框架版本對應的引用程式集。 這同樣適用于使用[引用](/visualstudio/msbuild/common-msbuild-project-items#reference)專案項直接將引用添加到 MSBuild 專案中：您只需指定程式集名稱，而無需指定完整檔路徑。 當您通過使用`-reference`編譯器選項（[在 C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md)和 Visual [Basic](../../visual-basic/reference/command-line-compiler/reference.md)中）或使用 Roslyn API<xref:Microsoft.CodeAnalysis.Compilation.AddReferences%2A?displayProperty=nameWithType>中的方法在命令列中添加對這些程式集的引用時，必須手動指定正確目標平臺版本的引用程式集檔。 .NET 框架參考程式集檔位於 *%程式檔 （x86）%\\引用\\程式集\\微軟\\框架 中。NETFramework*目錄。 對於 .NET Core，通過將`PreserveCompilationContext`專案屬性設置為`true`，可以強制發佈操作將目標平臺的引用程式集複製到輸出目錄的*發佈/refs*子目錄中。 然後，您可以將這些引用程式集檔傳遞給編譯器。 使用`DependencyContext` [Microsoft.擴展.依賴模型](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/)包可以説明查找其路徑。

因為它們不包含實現，因此無法載入引用程式集以執行。 嘗試這樣做會導致 。 <xref:System.BadImageFormatException?displayProperty=nameWithType> 如果要檢查引用程式集的內容，可以將其載入到 .NET 框架中的僅反射上下文（使用<xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType>方法）或<xref:System.Reflection.MetadataLoadContext>in .NET Core 中。

## <a name="generating-reference-assemblies"></a>生成引用程式集

當庫消費者需要根據許多不同版本的庫構建其程式時，為庫生成引用程式集非常有用。 分發所有這些版本的實現程式集可能由於其大大小而不切實際。 參考程式集的大小較小，將它們分發到庫的 SDK 中會減小下載大小並節省磁碟空間。

IDI 和生成工具還可以利用參考程式集來縮短包含多個類庫的大型解決方案的生成時間。 通常，在增量生成方案中，當專案的任何輸入檔（包括它所依賴的程式集）發生更改時，將重新生成專案。 每當程式師更改任何成員的實現時，實現程式集都會更改。 僅當其公共 API 受到影響時，引用程式集才會更改。 因此，在某些情況下，使用引用程式集作為輸入檔而不是實現程式集允許跳過從屬專案的生成。

您可以生成引用程式集：

- 在 MSBuild 專案中，通過使用[`ProduceReferenceAssembly`專案屬性](/visualstudio/msbuild/common-msbuild-project-properties)。
- `-refonly`從命令列編譯器時，通過指定 （[C#](../../csharp/language-reference/compiler-options/refonly-compiler-option.md) / [視覺基本](../../visual-basic/reference/command-line-compiler/refonly-compiler-option.md)）`-refout`或 （[C#](../../csharp/language-reference/compiler-options/refout-compiler-option.md) / [視覺化基本](../../visual-basic/reference/command-line-compiler/refout-compiler-option.md)） 編譯器選項。
- 使用 Roslyn API 時，<xref:Microsoft.CodeAnalysis.Emit.EmitOptions.EmitMetadataOnly?displayProperty=nameWithType>通過`true`設置<xref:Microsoft.CodeAnalysis.Emit.EmitOptions.IncludePrivateMembers?displayProperty=nameWithType>到`false`和 到 傳遞給<xref:Microsoft.CodeAnalysis.Compilation.Emit%2A?displayProperty=nameWithType>方法的物件。

如果要使用 NuGet 包分發引用程式集，則必須將它們包含在包目錄下的*ref\\*子目錄中，而不是用於實現程式集的*lib\\*子目錄中。

## <a name="reference-assemblies-structure"></a>參考程式集結構

引用程式集是相關概念（*僅中繼資料程式集）的*擴展。 僅中繼資料組件以單一的 `throw null` 主體取代其方法主體，但包含匿名型別以外的所有成員。 使用`throw null`實體（而不是沒有實體）的原因是**PEVerify**可以運行和傳遞（從而驗證中繼資料的完整性）。

參考組件會進一步移除來自僅中繼資料組件的中繼資料 (私用成員)：

- 參考組件只有在 API 介面中所需項目的參考。 實際的組件可能有與特定實作相關的其他參考。 例如，的`class C { private void M() { dynamic d = 1; ... } }`引用程式集不引用 所需的`dynamic`任何類型。
- 如果移除它們不會明顯影響編譯的話，則會移除私用函式的成員 (方法、屬性和事件)。 如果沒有[內部可見到](xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute)屬性，也會刪除內建函式成員。

引用程式集中的中繼資料繼續保留以下資訊：

- 所有類型，包括私有類型和巢狀型別。
- 所有屬性，甚至是內部屬性。
- 所有虛擬方法。
- 明確介面實作。
- 顯式實現的屬性和事件，因為它們的訪問器是虛擬的。
- 結構的所有欄位。

參考程式集包括程式集級[參考程式集](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)屬性。 此屬性可以在源中指定;但是，此屬性可以在源中指定。然後編譯器不需要合成它。 由於此屬性，運行時將拒絕載入引用程式集以執行（但它們可以在僅反射模式下載入）。

確切的引用程式集結構詳細資訊取決於編譯器版本。 如果較新版本被確定為不影響公共 API 表面，則可能會選擇排除更多中繼資料。

> [!NOTE]
> 本節中的資訊僅適用于 Roslyn 編譯器從 C# 版本 7.1 或 Visual Basic 版本 15.3 開始的引用程式集。 .NET 框架和 .NET 核心庫的引用程式集的結構在某些細節上可能有所不同，因為它們使用它們自己的生成引用程式集的機制。 例如，它們可能具有完全空的方法體，而不是`throw null`正文。 但一般原則仍然適用：它們沒有可用的方法實現，並且僅包含從公共 API 角度具有可觀察影響的成員的中繼資料。

## <a name="see-also"></a>另請參閱

- [.NET 中的組件](index.md)
- [Framework 目標概觀](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [如何：使用參考管理器添加或刪除引用](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)
