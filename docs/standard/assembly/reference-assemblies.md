---
title: 參考組件
description: 瞭解參考元件，這是 .NET 中只包含程式庫公用 API 介面的特殊元件類型
author: MSDN-WhiteKnight
ms.date: 09/12/2019
ms.openlocfilehash: 2f7f026c7fca4b772be85671dcc3a2a6d50a385c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831048"
---
# <a name="reference-assemblies"></a>參考組件

*參考元件* 是一種特殊類型的元件，其中只包含代表程式庫公用 API 介面所需的最少量中繼資料。 它們包括在組建工具中參考元件時，所有重要成員的宣告，但排除對其 API 合約沒有任何影響的私用成員的所有成員執行和宣告。 相反地，一般元件稱為「 *實元件*」。

無法載入參考元件來執行，但是可以用與實元件相同的方式，將它們當作編譯器輸入來傳遞。 參考元件通常會與特定平臺或程式庫 (SDK) 的軟體發展工具組一起散發。

使用參考元件可讓開發人員建立以特定程式庫版本為目標的程式，而不會有該版本的完整實元件。 假設您的電腦上只有一些程式庫的最新版本，但您想要建立以該程式庫舊版為目標的程式。 如果您直接針對實程式元件進行編譯，您可能會不小心使用先前版本中無法使用的 API 成員。 在目的電腦上測試程式時，您只會發現這個錯誤。 如果您針對較早版本的參考元件進行編譯，您將會立即收到編譯時期錯誤。

參考元件也可以代表合約，也就是一組未對應到具體實元件的 Api。 這類稱為 *合約元件* 的參考元件可以用來將多個平臺的目標設定為支援相同的 api 集。 例如，.NET Standard 提供合約元件 *netstandard.dll*，代表在不同 .net 平臺之間共用的一組通用 api。 這些 Api 的執行是包含在不同平臺上的不同元件中，例如在 .NET Framework 上的 *mscorlib.dll* 或 .net Core 上的 *System.Private.CoreLib.dll* 。 以 .NET Standard 為目標的程式庫可以在支援 .NET Standard 的所有平臺上執行。

## <a name="using-reference-assemblies"></a>使用參考元件

若要從您的專案使用特定 Api，您必須將參考加入其元件中。 您可以新增對實元件或參考元件的參考。 建議您在每次有參考元件時使用。 這麼做可確保您只會在目標版本中使用支援的 API 成員，以供 API 設計師使用。 使用參考元件可確保您不會依賴執行的詳細資料。

.NET Framework 程式庫的參考元件會以目標套件來散發。 您可以下載獨立安裝程式，或在 Visual Studio 安裝程式中選取元件來取得它們。 如需詳細資訊，請參閱 [安裝適用于開發人員的 .NET Framework](../../framework/install/guide-for-developers.md)。 若是 .NET Core 和 .NET Standard，參考元件會視需要自動下載， (透過 NuGet) 並加以參考。 針對 .NET Core 3.0 和更新版本，核心架構的參考元件會在 NETCore 中，而不是使用 3.0) 之前的版本，而是使用 ([Microsoft.NETCore.App.Ref](https://www.nuget.org/packages/Microsoft.NETCore.App.Ref) [套件。](https://www.nuget.org/packages/Microsoft.NETCore.App)

當您使用 [ **加入參考** ] 對話方塊在 Visual Studio 中新增 .NET Framework 元件的參考時，您會從清單中選取元件，而 Visual Studio 會自動尋找對應至您專案中所選取之目標 Framework 版本的參考元件。 同樣適用于使用  [參考](/visualstudio/msbuild/common-msbuild-project-items#reference) 專案專案直接將參考新增至 MSBuild 專案：您只需要指定元件名稱，而不是完整檔案路徑。 當您在命令列中使用 `-reference` 編譯器選項 ([在 c #](../../csharp/language-reference/compiler-options/reference-compiler-option.md) 和 [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md)) 或使用 Roslyn API 中的方法來新增這些元件的參考時 <xref:Microsoft.CodeAnalysis.Compilation.AddReferences%2A?displayProperty=nameWithType> ，您必須手動指定正確目標平臺版本的參考元件檔。 .NET Framework 參考元件檔位於 *% ProgramFiles (x86) % \\ reference 元件 \\ Microsoft \\ Framework \\ 。.Netframework* 目錄。 若是 .NET Core，您可以藉由將專案屬性設定為，強制發行作業將目標平臺的參考元件複製到輸出目錄的 *發行/refs* 子目錄中 `PreserveCompilationContext` `true` 。 然後，您可以將這些參考元件檔傳遞給編譯器。 使用 `DependencyContext` [DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/) 套件可協助找出其路徑。

因為它們不包含任何執行，所以無法載入參考元件以執行。 嘗試這麼做會導致 <xref:System.BadImageFormatException?displayProperty=nameWithType> 。 如果您想要檢查參考元件的內容，您可以使用) 的方法，將它載入至僅限反映的內容，並將它載入 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> 至 <xref:System.Reflection.MetadataLoadContext> .net Core 中的 .NET Framework (。

## <a name="generating-reference-assemblies"></a>產生參考元件

當您的程式庫取用者需要針對許多不同的程式庫版本建立程式時，產生程式庫的參考元件會很有用。 因為這些版本的大小很大，所以散發這些版本的實作為元件可能不切實際。 參考元件的大小較小，而將它們發佈為程式庫 SDK 的一部分，可減少下載大小並節省磁碟空間。

Ide 和組建工具也可以利用參考元件，以在由多個類別庫組成的大型方案時減少組建時間。 通常，在累加式組建案例中，專案會在其任何輸入檔變更時重建，包括它所相依的元件。 每次程式設計師變更任何成員的執行時，就會變更實組元件。 只有在參考元件的公用 API 受到影響時，參考元件才會變更。 因此，在某些情況下，使用參考元件做為輸入檔（而非實作為元件）可略過相依專案的組建。

您可以產生參考元件：

- 在 MSBuild 專案中，使用[ `ProduceReferenceAssembly` 專案屬性](/visualstudio/msbuild/common-msbuild-project-properties)。
- 從命令列編譯器時，指定 `-refonly` ([c #](../../csharp/language-reference/compiler-options/refonly-compiler-option.md)  /  [Visual Basic](../../visual-basic/reference/command-line-compiler/refonly-compiler-option.md) ) 或 `-refout` ([c #](../../csharp/language-reference/compiler-options/refout-compiler-option.md)  /  [Visual Basic](../../visual-basic/reference/command-line-compiler/refout-compiler-option.md)) 編譯器選項。
- 使用 Roslyn API 時， <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.EmitMetadataOnly?displayProperty=nameWithType> `true` <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.IncludePrivateMembers?displayProperty=nameWithType> `false` 在傳遞至方法的物件中將設定為和 <xref:Microsoft.CodeAnalysis.Compilation.Emit%2A?displayProperty=nameWithType> 。

如果您想要使用 NuGet 套件散發參考元件，則必須將它們包含在封裝目錄下的 *ref \\* 子目錄中，而不是在用於實元件的 *lib \\* 子目錄中。

## <a name="reference-assemblies-structure"></a>參考元件結構

參考元件是相關概念的擴充，也就是 *僅中繼資料的元件*。 僅中繼資料組件以單一的 `throw null` 主體取代其方法主體，但包含匿名型別以外的所有成員。 使用 `throw null` 主體 (而不是) 主體的原因，是為了讓 **PEVerify** 可以執行並通過 (，進而驗證中繼資料) 的完整性。

參考組件會進一步移除來自僅中繼資料組件的中繼資料 (私用成員)：

- 參考組件只有在 API 介面中所需項目的參考。 實際的組件可能有與特定實作相關的其他參考。 例如，的參考元件 `class C { private void M() { dynamic d = 1; ... } }` 不會參考所需的任何類型 `dynamic` 。
- 如果移除它們不會明顯影響編譯的話，則會移除私用函式的成員 (方法、屬性和事件)。 如果沒有 [InternalsVisibleTo](xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute) 屬性，則也會移除內建函式成員。

參考元件中的中繼資料會繼續保留下列資訊：

- 所有類型，包括私用和巢狀型別。
- 所有屬性，甚至是內部屬性。
- 所有虛擬方法。
- 明確的介面實現。
- 明確實作為屬性和事件，因為其存取子是虛擬的。
- 結構的所有欄位。

參考元件包含元件層級的 [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) 屬性。 這個屬性可以在來源中指定;然後編譯器不需要合成它。 由於這個屬性的原因，執行時間會拒絕載入參考元件以執行 (但可以在僅限反映模式中載入) 。

確切的參考元件結構詳細資料取決於編譯器版本。 如果較新的版本被判定為不影響公用 API 介面，則可選擇排除更多中繼資料。

> [!NOTE]
> 本節中的資訊僅適用于從 c # 7.1 版或 Visual Basic 版本15.3 開始的 Roslyn 編譯器所產生的參考元件。 .NET Framework 和 .NET Core 程式庫之參考元件的結構可能會因某些細節而異，因為它們會使用自己產生參考元件的機制。 例如，它們可能會有完全空白的方法主體，而不是 `throw null` 主體。 但一般原則仍然適用：它們沒有可使用的方法執行，而且只包含對公用 API 觀點有明顯影響的成員的中繼資料。

## <a name="see-also"></a>請參閱

- [.NET 中的組件](index.md)
- [Framework 目標概觀](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [如何：使用參考管理員新增或移除參考](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)
