---
title: 程式碼分析規則的設定檔
description: 瞭解不同的設定檔，以設定程式碼分析規則。
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 0d64df42ffb1763afed3e883c4f043755e158489
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633984"
---
# <a name="configuration-files-for-code-analysis-rules"></a><span data-ttu-id="8a1d3-103">程式碼分析規則的設定檔</span><span class="sxs-lookup"><span data-stu-id="8a1d3-103">Configuration files for code analysis rules</span></span>

<span data-ttu-id="8a1d3-104">程式碼分析規則有各種不同的設定 [選項](configuration-options.md)。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-104">Code analysis rules have various [configuration options](configuration-options.md).</span></span> <span data-ttu-id="8a1d3-105">您可以在下列其中一個分析器設定檔中，將這些選項指定為索引鍵/值組：</span><span class="sxs-lookup"><span data-stu-id="8a1d3-105">You specify these options as key-value pairs in one of the following analyzer configuration files:</span></span>

- <span data-ttu-id="8a1d3-106">[EditorConfig](#editorconfig) 檔案：以檔案為基礎或以資料夾為基礎的設定選項。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-106">[EditorConfig](#editorconfig) file: File-based or folder-based configuration options.</span></span>
- <span data-ttu-id="8a1d3-107">[全域 AnalyzerConfig](#global-analyzerconfig) 檔：專案層級的設定選項。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-107">[Global AnalyzerConfig](#global-analyzerconfig) file: Project-level configuration options.</span></span>

## EditorConfig

<span data-ttu-id="8a1d3-108">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) 檔案是用來提供 **適用于特定原始程式檔或資料夾的選項**。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-108">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) files are used to provide **options that apply to specific source files or folders**.</span></span> <span data-ttu-id="8a1d3-109">選項會放置在區段標頭下，以識別適用的檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-109">Options are placed under section headers to identify the applicable files and folders.</span></span> <span data-ttu-id="8a1d3-110">為您要設定的每個規則加入一個專案，並將它放在對應的副檔名區段下，例如 `[*.cs]` 。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-110">Add an entry for each rule you want to configure, and place it under the corresponding file extension section, for example, `[*.cs]`.</span></span>

```ini
[*.cs]
<option_name> = <option_value>
```

<span data-ttu-id="8a1d3-111">在上述範例中， `[*.cs]` 是一個 editorconfig 區段標頭，可選取目前資料夾內副檔名為 file 的所有 c # 檔案 `.cs` ，包括子資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-111">In the above example, `[*.cs]` is an editorconfig section header to select all C# files with `.cs` file extension within the current folder, including subfolders.</span></span> <span data-ttu-id="8a1d3-112">後續的專案 `<option_name> = <option_value>` 是分析器選項，將會套用至所有 c # 檔案。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-112">The subsequent entry, `<option_name> = <option_value>`, is an analyzer option that will be applied to all the C# files.</span></span>

<span data-ttu-id="8a1d3-113">您可以藉 EditorConfig 由將檔案放在對應的目錄中，將檔案慣例套用至資料夾、專案或整個存放庫。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-113">You can apply EditorConfig file conventions to a folder, a project, or an entire repo by placing the file in the corresponding directory.</span></span> <span data-ttu-id="8a1d3-114">這些選項會在組建階段執行分析時，以及您在 Visual Studio 中編輯程式碼時套用。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-114">These options are applied when executing the analysis at build time and while you edit code in Visual Studio.</span></span>

<span data-ttu-id="8a1d3-115">如果您有現有的 *editorconfig* 檔案可用於編輯器設定，例如縮排大小或是否要修剪尾端空白字元，則可以將您的程式碼分析設定選項放在相同的檔案中。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-115">If you have an existing *.editorconfig* file for editor settings such as indent size or whether to trim trailing whitespace, you can place your code analysis configuration options in the same file.</span></span>

> [!TIP]
> <span data-ttu-id="8a1d3-116">Visual Studio 提供 *editorconfig* 專案範本，可讓您輕鬆地將其中一個檔案新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-116">Visual Studio provides an *.editorconfig* item template that makes is easy to add one of these files to your project.</span></span> <span data-ttu-id="8a1d3-117">如需詳細資訊，請參閱 [將檔案新增 EditorConfig 至專案](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project)。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-117">For more information, see [Add an EditorConfig file to a project](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).</span></span>

### <a name="example"></a><span data-ttu-id="8a1d3-118">範例</span><span class="sxs-lookup"><span data-stu-id="8a1d3-118">Example</span></span>

<span data-ttu-id="8a1d3-119">以下是 EditorConfig 設定選項和規則嚴重性的範例檔案：</span><span class="sxs-lookup"><span data-stu-id="8a1d3-119">Following is an example EditorConfig file to configure options and rule severity:</span></span>

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="global-analyzerconfig"></a><span data-ttu-id="8a1d3-120">Global AnalyzerConfig</span><span class="sxs-lookup"><span data-stu-id="8a1d3-120">Global AnalyzerConfig</span></span>

<span data-ttu-id="8a1d3-121">從支援 Visual Studio 2019 16.8 版和更新版本) 的 .NET 5 SDK (，您也可以使用全域 _AnalyzerConfig_ 檔來設定分析器選項。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-121">Starting with the .NET 5 SDK (which is supported in Visual Studio 2019 version 16.8 and later versions), you can also configure analyzer options with global _AnalyzerConfig_ files.</span></span> <span data-ttu-id="8a1d3-122">這些檔案是用來提供套用 **至專案中所有原始** 程式檔的選項，而不論其檔案名或檔案路徑為何。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-122">These files are used to provide **options that apply to all the source files in a project**, regardless of their file names or file paths.</span></span>

<span data-ttu-id="8a1d3-123">與檔案不同的 [EditorConfig](#editorconfig) 是，全域設定檔案不能用來設定 ide 的編輯器樣式設定，例如縮排大小或是否修剪尾端空白。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-123">Unlike [EditorConfig](#editorconfig) files, global config files can't be used to configure editor style settings for IDEs, such as indent size or whether to trim trailing whitespace.</span></span> <span data-ttu-id="8a1d3-124">相反地，它們是專門用來指定專案層級的分析器設定選項。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-124">Instead, they are designed purely for specifying project-level analyzer configuration options.</span></span>

### <a name="format"></a><span data-ttu-id="8a1d3-125">格式</span><span class="sxs-lookup"><span data-stu-id="8a1d3-125">Format</span></span>

<span data-ttu-id="8a1d3-126">不同 EditorConfig 于需要區段標頭的檔案，例如 `[*.cs]` ，若要識別適用的檔案和資料夾，全域 AnalyzerConfig 檔案沒有區段標頭。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-126">Unlike EditorConfig files, which must have section headers, such as `[*.cs]`, to identify the applicable files and folders, global AnalyzerConfig files don't have section headers.</span></span> <span data-ttu-id="8a1d3-127">相反地，他們需要表單的最上層專案， `is_global = true` 才能與一般檔案區別 EditorConfig 。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-127">Instead, they require a top level entry of the form `is_global = true` to differentiate them from regular EditorConfig files.</span></span> <span data-ttu-id="8a1d3-128">這表示檔案中的所有選項都適用于整個專案。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-128">This indicates that all the options in the file apply to the entire project.</span></span> <span data-ttu-id="8a1d3-129">例如：</span><span class="sxs-lookup"><span data-stu-id="8a1d3-129">For example:</span></span>

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a><span data-ttu-id="8a1d3-130">命名</span><span class="sxs-lookup"><span data-stu-id="8a1d3-130">Naming</span></span>

<span data-ttu-id="8a1d3-131">不同 EditorConfig 于必須命名的檔案， `.editorconfig` 全域設定檔不需要有特定的名稱或副檔名。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-131">Unlike EditorConfig files, which must be named `.editorconfig`, global config files do not need to have a specific name or extension.</span></span> <span data-ttu-id="8a1d3-132">但是，如果您將這些檔案命名為，就會隱含地將這些檔案套用 `.globalconfig` 至目前資料夾（包括子資料夾）中的所有 c # 和 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-132">However, if you name these files as `.globalconfig` then they will be implicitly applied to all the C# and Visual Basic projects within the current folder, including subfolders.</span></span> <span data-ttu-id="8a1d3-133">否則，您必須明確地將 `GlobalAnalyzerConfigFiles` 專案新增至 MSBuild 專案檔：</span><span class="sxs-lookup"><span data-stu-id="8a1d3-133">Otherwise, you must explicitly add the `GlobalAnalyzerConfigFiles` item to your MSBuild project file:</span></span>

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="8a1d3-134">即使檔案已命名，也需要最上層專案 `is_global = true` `.globalconfig` 。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-134">The top-level entry `is_global = true` is required even when the file is named `.globalconfig`.</span></span>

### <a name="example"></a><span data-ttu-id="8a1d3-135">範例</span><span class="sxs-lookup"><span data-stu-id="8a1d3-135">Example</span></span>

<span data-ttu-id="8a1d3-136">以下是在專案層級設定選項和規則嚴重性的範例全域 AnalyzerConfig 檔案：</span><span class="sxs-lookup"><span data-stu-id="8a1d3-136">Following is an example global AnalyzerConfig file to configure options and rule severity at the project level:</span></span>

```ini
# Top level entry required to mark this as a global AnalyzerConfig file
is_global = true

# NOTE: No section headers for configuration entries

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="precedence"></a><span data-ttu-id="8a1d3-137">優先順序</span><span class="sxs-lookup"><span data-stu-id="8a1d3-137">Precedence</span></span>

<span data-ttu-id="8a1d3-138">檔案 EditorConfig 和全域 AnalyzerConfig 檔都會指定每個選項的機碼值組。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-138">Both EditorConfig files and global AnalyzerConfig files specify a key-value pair for each option.</span></span> <span data-ttu-id="8a1d3-139">如果有多個專案具有相同的索引鍵，但有不同的值，就會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-139">Conflicts arise when there are multiple entries with the same key but different values.</span></span>

### <a name="general-options"></a><span data-ttu-id="8a1d3-140">一般選項</span><span class="sxs-lookup"><span data-stu-id="8a1d3-140">General options</span></span>

<span data-ttu-id="8a1d3-141">當選項之間發生衝突時，會使用下列優先順序規則來解決衝突：</span><span class="sxs-lookup"><span data-stu-id="8a1d3-141">When conflicts arise between options, the following precedence rules are used to resolve the conflicts:</span></span>

- <span data-ttu-id="8a1d3-142">相同設定檔中的衝突專案：在檔案中稍後出現的專案會獲勝。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-142">Conflicting entries in the same configuration file: The entry that appears later in the file wins.</span></span> <span data-ttu-id="8a1d3-143">這適用于單一檔案中的衝突專案 EditorConfig ，也適用于單一全域 AnalyzerConfig 檔案內。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-143">This is true for conflicting entries within a single EditorConfig file and also within a single global AnalyzerConfig file.</span></span>

- <span data-ttu-id="8a1d3-144">兩個檔案中有衝突的專案 EditorConfig ：檔案系統中更深入的檔案專案 EditorConfig ，因此有較長的檔案路徑，wins。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-144">Conflicting entries in two EditorConfig files: The entry in the EditorConfig file that's deeper in the file system, and hence has a longer file path, wins.</span></span>

- <span data-ttu-id="8a1d3-145">兩個全域 AnalyzerConfig 檔中的衝突專案：會報告編譯器警告，並忽略這兩個專案。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-145">Conflicting entries in two global AnalyzerConfig files: A compiler warning is reported and both entries are ignored.</span></span>

- <span data-ttu-id="8a1d3-146">檔案 EditorConfig 和全域 AnalyzerConfig 檔中的衝突專案：檔案中的專案 EditorConfig 獲勝。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-146">Conflicting entries in an EditorConfig file and a Global AnalyzerConfig file: The entry in the EditorConfig file wins.</span></span>

### <a name="severity-options"></a><span data-ttu-id="8a1d3-147">嚴重性選項</span><span class="sxs-lookup"><span data-stu-id="8a1d3-147">Severity options</span></span>

<span data-ttu-id="8a1d3-148">先前的 [一般優先順序規則](#general-options) 適用于設定檔中指定的所有選項。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-148">The previous [general precedence rules](#general-options) apply for all options specified in configuration files.</span></span> <span data-ttu-id="8a1d3-149">針對 [嚴重性](configuration-options.md#severity-level) 設定選項，適用下列額外的優先順序規則：</span><span class="sxs-lookup"><span data-stu-id="8a1d3-149">For [severity configuration](configuration-options.md#severity-level) options, the following additional precedence rules apply:</span></span>

- <span data-ttu-id="8a1d3-150">在命令列中指定為編譯器選項的嚴重性選項 (`/nowarn` 或 `/warnaserror`) 一律覆寫在和全域 AnalyzerConfig 檔中指定的 [嚴重性](configuration-options.md#severity-level) 設定選項 EditorConfig 。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-150">Severity options specified at the command line as compiler options (`/nowarn` or `/warnaserror`) always override [severity configuration](configuration-options.md#severity-level) options specified in EditorConfig and global AnalyzerConfig files.</span></span>

- <span data-ttu-id="8a1d3-151">您也可以使用 [規則集](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) 檔案來指定嚴重性選項。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-151">Severity options can also be specified with a [Ruleset](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) file.</span></span> <span data-ttu-id="8a1d3-152">不過，規則集檔案已被取代 EditorConfig ，並使用全域 AnalyzerConfig 檔。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-152">However, rulesets files are deprecated in favor of EditorConfig and global AnalyzerConfig files.</span></span> <span data-ttu-id="8a1d3-153">建議您 [將規則集檔案轉換成相等的檔案 EditorConfig ](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file)。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-153">It's recommended that you [convert ruleset files to an equivalent EditorConfig file](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file).</span></span> <span data-ttu-id="8a1d3-154">規則集檔案和或全域 AnalyzerConfig 檔中的衝突嚴重性專案的優先順序未 EditorConfig _定義_。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-154">Precedence for conflicting severity entries from a ruleset file and EditorConfig or global AnalyzerConfig files is _undefined_.</span></span>

- <span data-ttu-id="8a1d3-155">如需具有不同索引鍵的相關嚴重性選項之優先順序規則的相關資訊（例如，針對單一規則指定不同的嚴重性，以及規則所屬的類別），請參閱程式 [代碼分析](configuration-options.md#precedence)的設定選項。</span><span class="sxs-lookup"><span data-stu-id="8a1d3-155">For information about precedence rules for related severity options with different keys, for example, when different severities are specified for a single rule and for the category that rule falls under, see [Configuration options for code analysis](configuration-options.md#precedence).</span></span>

## <a name="see-also"></a><span data-ttu-id="8a1d3-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a1d3-156">See also</span></span>

- [<span data-ttu-id="8a1d3-157">EditorConfig vs global AnalyzerConfig 設計問題</span><span class="sxs-lookup"><span data-stu-id="8a1d3-157">EditorConfig vs global AnalyzerConfig design issue</span></span>](https://github.com/dotnet/roslyn/issues/47707)
