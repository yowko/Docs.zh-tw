---
title: 如何:使用中繼資料載入中文檢查程式集內容
description: 瞭解如何使用中繼資料 LoadContext,這是 API,讓您能夠載入 .NET 程式集以進行檢查。
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: d2589d51a6e0611504c0133d293d3fdfae32553c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242656"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>如何:使用中繼資料載入中文檢查程式集內容

默認情況下,.NET 中的反射 API 使開發人員能夠檢查載入主執行上下文中的程式集的內容。 但是,有時無法將程式集載入到執行上下文中,例如,因為它是為另一個平臺或處理器體系結構編譯的,或者它是[一個引用程式集](reference-assemblies.md)。 API<xref:System.Reflection.MetadataLoadContext?displayProperty=fullName>允許您載入和檢查此類程式集。 載入的<xref:System.Reflection.MetadataLoadContext>程式集僅被視為元數據,也就是說,可以檢查程式集中的類型,但不能執行其中包含的任何代碼。 與主執行上下文不同,不會<xref:System.Reflection.MetadataLoadContext>自動載入來自當前目錄的依賴項;因此,不會從當前目錄中載入依賴項。相反,它使用傳遞給它提供的<xref:System.Reflection.MetadataAssemblyResolver>自定義綁定邏輯。

## <a name="prerequisites"></a>Prerequisites

要使用<xref:System.Reflection.MetadataLoadContext>,請安裝[系統。反射.元數據載入上下文](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext)NuGet 包。 它支援任何 .NET 標準 2.0 標準,例如 .NET 核心 2.0 或 .NET 框架 4.6.1。

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>為中繼資料載入中建立中繼資料程式集解析器

創建<xref:System.Reflection.MetadataLoadContext>需要提供的<xref:System.Reflection.MetadataAssemblyResolver>實例。 提供一個最簡單的方法是使用,<xref:System.Reflection.PathAssemblyResolver>它解析來自給定程式集路徑字串集合中的程式集。 除了要直接檢查的程式集之外,此集合還應包含所有所需的依賴項。 例如,要讀取位於外部程式集中的自定義屬性,應包含該程式集,否則將引發異常。 在大多數情況下,應至少包括*核心程式集*,即包含內建系統類型的程式集,如<xref:System.Object?displayProperty=nameWithType>。 以下程式碼示範<xref:System.Reflection.PathAssemblyResolver>如何 使用由已檢查程式集與目前執行時的核心程式集組成的集合建立:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

如果需要存取所有 BCL 類型,可以在集合中包括所有運行時程式集。 以下程式碼示範<xref:System.Reflection.PathAssemblyResolver>如何 使用由已檢查的程式集與目前執行時的所有程式集組成的集合建立:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>建立中繼資料載入中文

要創建<xref:System.Reflection.MetadataLoadContext>調用其建構函<xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>數 ,將以前<xref:System.Reflection.MetadataAssemblyResolver>創建的 參數傳遞為第一個參數,將核心程式集名稱傳遞給第二個參數。 您可以省略核心程式集名稱,在這種情況下,構造函數將嘗試使用預設名稱:"mscorlib"、"System.Runtime"或"net標準"。

創建上下文後,可以使用方法(如<xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>) 將程式集載入其中。 您可以在載入的程式集上使用所有反射 API,但涉及代碼執行的程式集除外。 該方法<xref:System.Reflection.MemberInfo.GetCustomAttributes%2A>確實涉及建構函數的執行,因此,當您需要在中<xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A>檢查 自訂屬性時,請<xref:System.Reflection.MetadataLoadContext>使用方法 。

以下代碼範例建立<xref:System.Reflection.MetadataLoadContext>,將程式集載入到控制台中,並將程式集屬性輸出到控制台中:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>範例

有關完整的程式碼範例,請參考[使用中繼資料載入的文字範例](https://github.com/dotnet/samples/tree/master/core/assembly/MetadataLoadContext)。
