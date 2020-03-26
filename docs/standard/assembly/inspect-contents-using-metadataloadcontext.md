---
title: 如何：使用中繼資料載入上下文檢查程式集內容
description: 瞭解如何使用中繼資料 LoadCoNtext，這是一個 API，使您能夠載入 .NET 程式集以進行檢查。
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: a782b2db4fb62cfaedaa6768e2131bda6bec864c
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80229298"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>如何：使用中繼資料載入上下文檢查程式集內容

預設情況下，.NET 中的反射 API 使開發人員能夠檢查載入到主執行上下文中的程式集的內容。 但是，有時無法將程式集載入到執行上下文中，例如，因為它是為另一個平臺或處理器體系結構編譯的，或者它是[一個引用程式集](reference-assemblies.md)。 API<xref:System.Reflection.MetadataLoadContext?displayProperty=fullName>允許您載入和檢查此類程式集。 載入到 的<xref:System.Reflection.MetadataLoadContext>程式集僅被視為中繼資料，也就是說，可以檢查程式集中的類型，但不能執行其中包含的任何代碼。 與主執行上下文不同，不會<xref:System.Reflection.MetadataLoadContext>自動載入來自目前的目錄的依賴項;因此，不會從目前的目錄中載入依賴項。相反，它使用傳遞給它提供的<xref:System.Reflection.MetadataAssemblyResolver>自訂綁定邏輯。

## <a name="prerequisites"></a>Prerequisites

要使用<xref:System.Reflection.MetadataLoadContext>，請安裝[系統。反射.中繼資料載入上下文](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext)NuGet 包。 它支援任何 .NET 標準 2.0 標準，例如 .NET 核心 2.0 或 .NET 框架 4.6.1。

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>為中繼資料載入上下文創建中繼資料程式集解析器

創建<xref:System.Reflection.MetadataLoadContext>需要提供 的<xref:System.Reflection.MetadataAssemblyResolver>實例。 提供一個最簡單的方法是使用 ，<xref:System.Reflection.PathAssemblyResolver>它解析來自給定程式集路徑字串集合中的程式集。 除了要直接檢查的程式集之外，此集合還應包含所有所需的依賴項。 例如，要讀取位於外部程式集中的自訂屬性，應包含該程式集，否則將引發異常。 在大多數情況下，應至少包括*核心程式集*，即包含內置系統類型的程式集，如<xref:System.Object?displayProperty=nameWithType>。 以下代碼演示如何<xref:System.Reflection.PathAssemblyResolver>使用由已檢查程式集和當前運行時的核心程式集組成的集合創建：

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

如果需要訪問所有 BCL 類型，可以在集合中包括所有運行時程式集。 以下代碼演示如何<xref:System.Reflection.PathAssemblyResolver>使用由已檢查的程式集和當前運行時的所有程式集組成的集合創建：

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>創建中繼資料載入上下文

要創建<xref:System.Reflection.MetadataLoadContext>調用其建構函式<xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>，將以前創建的<xref:System.Reflection.MetadataAssemblyResolver>參數傳遞為第一個參數，將核心程式集名稱傳遞給第二個參數。 您可以省略核心程式集名稱，在這種情況下，建構函式將嘗試使用預設名稱："mscorlib"、"System.Runtime"或"net標準"。

創建上下文後，可以使用 方法（如<xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>） 將程式集載入到其中。 您可以在載入的程式集上使用所有反射 API，但涉及代碼執行的程式集除外。 該方法<xref:System.Reflection.MemberInfo.GetCustomAttributes%2A>確實涉及建構函式的執行，因此，當您需要在 中檢查<xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A>自訂屬性時，請使用 方法<xref:System.Reflection.MetadataLoadContext>。

以下代碼示例創建<xref:System.Reflection.MetadataLoadContext>，將程式集載入到主控台中，並將程式集屬性輸出到主控台中：

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>範例

有關完整的代碼示例，請參閱[使用中繼資料載入上下文檢查程式集內容](https://docs.microsoft.com/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/)。
