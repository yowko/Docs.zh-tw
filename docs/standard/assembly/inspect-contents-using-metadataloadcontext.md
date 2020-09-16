---
title: 如何：使用 MetadataLoadCoNtext 檢查元件內容
description: 瞭解如何使用 MetadataLoadCoNtext，這是可讓您載入 .NET 元件以供檢查之用的 API。
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 7f90149a98632ea57e8d241a0ccdf4b50264ac5c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552020"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>如何：使用 MetadataLoadCoNtext 檢查元件內容

.NET 中的反映 API 預設可讓開發人員檢查載入主要執行內容中的元件內容。 不過，有時您無法將元件載入執行內容，例如，因為它是針對另一個平臺或處理器架構所編譯，或是 [參考元件](reference-assemblies.md)。 <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName>API 可讓您載入和檢查這類元件。 載入至的元件 <xref:System.Reflection.MetadataLoadContext> 只會被視為中繼資料，也就是說，您可以檢查元件中的類型，但無法執行其中包含的任何程式碼。 與主要執行內容不同的是， <xref:System.Reflection.MetadataLoadContext> 不會自動載入目前目錄中的相依性，而是會使用 <xref:System.Reflection.MetadataAssemblyResolver> 傳遞給它的自訂系結邏輯。

## <a name="prerequisites"></a>必要條件

若要使用 <xref:System.Reflection.MetadataLoadContext> ，請安裝 [MetadataLoadCoNtext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) NuGet 套件。 .NET Standard 符合2.0 規範的目標 framework （例如 .NET Core 2.0 或 .NET Framework 4.6.1）均可支援。

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>建立 MetadataLoadCoNtext 的 MetadataAssemblyResolver

建立 <xref:System.Reflection.MetadataLoadContext> 需要提供的實例 <xref:System.Reflection.MetadataAssemblyResolver> 。 提供一個最簡單的方法是使用 <xref:System.Reflection.PathAssemblyResolver> ，它會解析元件路徑字串之指定集合的元件。 除了您要直接檢查的元件之外，此集合也應該包含所有必要的相依性。 例如，若要讀取位於外部元件中的自訂屬性，您應該包含該元件，否則會擲回例外狀況。 在大部分的情況下，您應該至少包含 *核心元件*，也就是包含內建系統類型的元件，例如 <xref:System.Object?displayProperty=nameWithType> 。 下列程式碼示範如何使用由已 <xref:System.Reflection.PathAssemblyResolver> 檢查元件和目前執行時間核心元件組成的集合來建立。

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

如果您需要所有 BCL 類型的存取權，您可以將所有執行時間元件包含在集合中。 下列程式碼示範如何 <xref:System.Reflection.PathAssemblyResolver> 使用由已檢查的元件和目前執行時間的所有元件所組成的集合來建立。

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>建立 MetadataLoadCoNtext

若要建立 <xref:System.Reflection.MetadataLoadContext> ，請叫用其函式 <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29> ，並將先前建立的 <xref:System.Reflection.MetadataAssemblyResolver> 視為第一個參數，並將核心元件名稱傳遞為第二個參數。 您可以省略核心元件名稱，在此情況下，此函式會嘗試使用預設名稱： "mscorlib.dll"、"system.string" 或 "netstandard"。

建立內容之後，您可以使用之類的方法將元件載入至其中 <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A> 。 您可以在載入的元件上使用所有反映 Api，但牽涉到程式碼執行的元件除外。 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A>方法會涉及執行的函式，因此 <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> 當您需要檢查中的自訂屬性時，請改用方法 <xref:System.Reflection.MetadataLoadContext> 。

下列程式碼範例 <xref:System.Reflection.MetadataLoadContext> 會建立、載入元件，並將元件屬性輸出到主控台：

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>範例

如需完整的程式碼範例，請參閱 [使用 MetadataLoadCoNtext 範例檢查元件內容](/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/)。
