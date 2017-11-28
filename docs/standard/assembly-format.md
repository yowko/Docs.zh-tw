---
title: ".NET 組件檔格式"
description: "了解用來描述並包含 .NET 應用程式和程式庫的 .NET 組件檔格式。"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: 797bd4a7c160feda69a3190d9e364b166a51c703
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="net-assembly-file-format"></a><span data-ttu-id="fef3b-104">.NET 組件檔格式</span><span class="sxs-lookup"><span data-stu-id="fef3b-104">.NET Assembly File Format</span></span>

<span data-ttu-id="fef3b-105">.NET 定義用來完整描述並包含 .NET 程式的二進位檔案格式 - "assembly"。</span><span class="sxs-lookup"><span data-stu-id="fef3b-105">.NET defines a binary file format - "assembly" - that is used to fully-describe and contain .NET programs.</span></span> <span data-ttu-id="fef3b-106">組件用於程式本身以及任何相依的程式庫。</span><span class="sxs-lookup"><span data-stu-id="fef3b-106">Assemblies are used for the programs themselves as well as any dependent libraries.</span></span> <span data-ttu-id="fef3b-107">除了適當的 .NET 實作之外，.NET 程式也可以執行為一或多個沒有其他必要成品的組件。</span><span class="sxs-lookup"><span data-stu-id="fef3b-107">A .NET program can be executed as one of more assemblies, with no other required artifacts, beyond the appropriate .NET implementation.</span></span> <span data-ttu-id="fef3b-108">雖然有時會使用這種格式 (例如，WinRT) 進行描述，但是原生相依性 (包括作業系統 API) 會有不同的考量，而且不會包含在 .NET 組件格式內。</span><span class="sxs-lookup"><span data-stu-id="fef3b-108">Native dependencies, including operating system APIs, are a separate concern and are not contained within the .NET assembly format, although are sometimes described with this format (for example, WinRT).</span></span>

> <span data-ttu-id="fef3b-109">每個 CLI 元件都會攜帶該元件特定宣告、實作和參考的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fef3b-109">Each CLI component carries the metadata for declarations, implementations, and references specific to that component.</span></span> <span data-ttu-id="fef3b-110">因此，元件特定中繼資料是指元件中繼資料，而且產生的元件即為來自 ECMA 335 I.9.1 的自我描述元件和組件。</span><span class="sxs-lookup"><span data-stu-id="fef3b-110">Therefore, the component-specific metadata is referred to as component metadata, and the resulting component is said to be self-describing – from ECMA 335 I.9.1, Components and assemblies.</span></span>

<span data-ttu-id="fef3b-111">格式會完整指定並標準化為 ECMA 335。</span><span class="sxs-lookup"><span data-stu-id="fef3b-111">The format is fully specified and standardized as ECMA 335.</span></span> <span data-ttu-id="fef3b-112">所有 .NET 編譯器和執行階段都會使用這種格式。</span><span class="sxs-lookup"><span data-stu-id="fef3b-112">All .NET compilers and runtimes use this format.</span></span> <span data-ttu-id="fef3b-113">所記載且不常更新之二進位格式的目前狀態已是互通性的主要優點 (即需求)。</span><span class="sxs-lookup"><span data-stu-id="fef3b-113">The presence of a documented and infrequently updated binary format has been a major benefit (arguably a requirement) for interoperatibility.</span></span> <span data-ttu-id="fef3b-114">這種格式上次在 2005 年進行重大更新 (.NET 2.0)，可容納泛型和處理器架構。</span><span class="sxs-lookup"><span data-stu-id="fef3b-114">The format was last updated in a substantive way in 2005 (.NET 2.0) to accommodate generics and processor architecture.</span></span>

<span data-ttu-id="fef3b-115">格式為 CPU 並且無作業系統無關。</span><span class="sxs-lookup"><span data-stu-id="fef3b-115">The format is CPU- and OS-agnostic.</span></span> <span data-ttu-id="fef3b-116">它已用作將目標設為許多晶片和 CPU 之 .NET 實作的一部分。</span><span class="sxs-lookup"><span data-stu-id="fef3b-116">It has been used as part of .NET implementations that target many chips and CPUs.</span></span> <span data-ttu-id="fef3b-117">雖然格式本身具有 Windows 傳承，但是可在任何作業系統上實作。</span><span class="sxs-lookup"><span data-stu-id="fef3b-117">While the format itself has Windows heritage, it is implementable on any operating system.</span></span> <span data-ttu-id="fef3b-118">作業系統互通性的最重大選擇就是大部分值都是以位元組由小到大格式儲存。</span><span class="sxs-lookup"><span data-stu-id="fef3b-118">It’s arguably most significant choice for OS interoperability is that most values are stored in little-endian format.</span></span> <span data-ttu-id="fef3b-119">它沒有電腦指標大小 (例如，32 位元、64 位元) 的特定同質性。</span><span class="sxs-lookup"><span data-stu-id="fef3b-119">It doesn’t have a specific affinity to machine pointer size (for example, 32-bit, 64-bit).</span></span>

<span data-ttu-id="fef3b-120">.NET 組件格式對於指定的程式或程式庫結構也具有相當的描述性。</span><span class="sxs-lookup"><span data-stu-id="fef3b-120">The .NET assembly format is also very descriptive about the structure of a given program or library.</span></span> <span data-ttu-id="fef3b-121">它會特別描述組件的內部元件︰定義的組件參考和類型，以及其內部結構。</span><span class="sxs-lookup"><span data-stu-id="fef3b-121">It describes the internal components of an assembly, specifically: assembly references and types defined and their internal structure.</span></span> <span data-ttu-id="fef3b-122">工具或 API 可以讀取和處理這項資訊以供顯示，或進行程式設計決策。</span><span class="sxs-lookup"><span data-stu-id="fef3b-122">Tools or APIs can read and process this information for display or to make programmatic decisions.</span></span>

## <a name="format"></a><span data-ttu-id="fef3b-123">格式</span><span class="sxs-lookup"><span data-stu-id="fef3b-123">Format</span></span>

<span data-ttu-id="fef3b-124">.NET 二進位格式是根據 Windows [PE 檔案](http://en.wikipedia.org/wiki/Portable_Executable)格式。</span><span class="sxs-lookup"><span data-stu-id="fef3b-124">The .NET binary format is based on the Windows [PE file](http://en.wikipedia.org/wiki/Portable_Executable) format.</span></span> <span data-ttu-id="fef3b-125">事實上，.NET 類別庫是一致的 Windows PE，並且顯示在第一次看到 Windows 動態連結程式庫 (DLL) 或應用程式執行檔 (EXE) 時。</span><span class="sxs-lookup"><span data-stu-id="fef3b-125">In fact, .NET class libraries are conformant Windows PEs, and appear on first glance to be Windows dynamic link libraries (DLLs) or application executables (EXEs).</span></span> <span data-ttu-id="fef3b-126">這是 Windows 上極為實用的特性，在此，它們可以偽裝為原生可執行二進位檔，並進行一些相同的處理 (例如，OS 載入、PE 工具)。</span><span class="sxs-lookup"><span data-stu-id="fef3b-126">This is a very useful characteristic on Windows, where they can masquerade as native executable binaries and get some of the same treatment (for example, OS load, PE tools).</span></span>

![組件標頭](./media/assembly-format/assembly-headers.png)

<span data-ttu-id="fef3b-128">來自 ECMA 335 II.25.1 的組件標頭 (執行階段檔案格式的結構)。</span><span class="sxs-lookup"><span data-stu-id="fef3b-128">Assembly Headers from ECMA 335 II.25.1, Structure of the runtime file format.</span></span>

## <a name="processing-the-assemblies"></a><span data-ttu-id="fef3b-129">處理組件</span><span class="sxs-lookup"><span data-stu-id="fef3b-129">Processing the Assemblies</span></span>

<span data-ttu-id="fef3b-130">可能會撰寫工具或 API 來處理組件。</span><span class="sxs-lookup"><span data-stu-id="fef3b-130">It is possible to write tools or APIs to process assemblies.</span></span> <span data-ttu-id="fef3b-131">組件資訊可在執行階段進行程式設計決策、重新撰寫組件、在編輯器中提供 API IntelliSense，以及產生文件。</span><span class="sxs-lookup"><span data-stu-id="fef3b-131">Assembly information enables making programmatic decisions at runtime, re-writing assemblies, providing API IntelliSense in an editor and generating documentation.</span></span> <span data-ttu-id="fef3b-132"><xref:System.Reflection?displayProperty=nameWithType> 和 [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) 是常用於此目的之工具的不錯範例。</span><span class="sxs-lookup"><span data-stu-id="fef3b-132"><xref:System.Reflection?displayProperty=nameWithType> and [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) are good examples of tools that are frequently used for this purpose.</span></span>
