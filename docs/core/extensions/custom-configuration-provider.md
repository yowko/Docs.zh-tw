---
title: 在 .NET 中執行自訂設定提供者
description: 瞭解如何在 .NET 應用程式中執行自訂設定提供者。
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.topic: how-to
ms.openlocfilehash: 968bf202eeea32742444681260d5ab0b27b403f9
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720746"
---
# <a name="implement-a-custom-configuration-provider-in-net"></a><span data-ttu-id="d52ae-103">在 .NET 中執行自訂設定提供者</span><span class="sxs-lookup"><span data-stu-id="d52ae-103">Implement a custom configuration provider in .NET</span></span>

<span data-ttu-id="d52ae-104">有許多設定 [提供者](configuration-providers.md) 可用於一般設定來源，例如 JSON、XML 和 INI 檔案。</span><span class="sxs-lookup"><span data-stu-id="d52ae-104">There are many [configuration providers](configuration-providers.md) available for common configuration sources such as JSON, XML, and INI files.</span></span> <span data-ttu-id="d52ae-105">當其中一個可用的提供者不符合您的應用程式需求時，您可能需要執行自訂設定提供者。</span><span class="sxs-lookup"><span data-stu-id="d52ae-105">You may need to implement a custom configuration provider when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="d52ae-106">在本文中，您將瞭解如何執行依賴資料庫做為其設定來源的自訂設定提供者。</span><span class="sxs-lookup"><span data-stu-id="d52ae-106">In this article, you'll learn how to implement a custom configuration provider that relies on a database as its configuration source.</span></span>

## <a name="custom-configuration-provider"></a><span data-ttu-id="d52ae-107">自訂設定提供者</span><span class="sxs-lookup"><span data-stu-id="d52ae-107">Custom configuration provider</span></span>

<span data-ttu-id="d52ae-108">範例應用程式示範如何建立基本的設定提供者，以使用 [Entity Framework (EF) Core](/ef/core)，從資料庫讀取設定機碼值組。</span><span class="sxs-lookup"><span data-stu-id="d52ae-108">The sample app demonstrates how to create a basic configuration provider that reads configuration key-value pairs from a database using [Entity Framework (EF) Core](/ef/core).</span></span>

<span data-ttu-id="d52ae-109">提供者具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="d52ae-109">The provider has the following characteristics:</span></span>

- <span data-ttu-id="d52ae-110">EF 記憶體內資料庫會用於示範用途。</span><span class="sxs-lookup"><span data-stu-id="d52ae-110">The EF in-memory database is used for demonstration purposes.</span></span> <span data-ttu-id="d52ae-111">若要使用需要連接字串的資料庫，請實作第二個 `ConfigurationBuilder` 以從另一個設定提供者提供連接字串。</span><span class="sxs-lookup"><span data-stu-id="d52ae-111">To use a database that requires a connection string, implement a secondary `ConfigurationBuilder` to supply the connection string from another configuration provider.</span></span>
- <span data-ttu-id="d52ae-112">啟動時，該提供者會將資料庫資料表讀入到設定中。</span><span class="sxs-lookup"><span data-stu-id="d52ae-112">The provider reads a database table into configuration at startup.</span></span> <span data-ttu-id="d52ae-113">該提供者不會以個別機碼為基礎查詢資料庫。</span><span class="sxs-lookup"><span data-stu-id="d52ae-113">The provider doesn't query the database on a per-key basis.</span></span>
- <span data-ttu-id="d52ae-114">未實作變更時重新載入，因此在應用程式啟動後更新資料庫對應用程式設定沒有影響。</span><span class="sxs-lookup"><span data-stu-id="d52ae-114">Reload-on-change isn't implemented, so updating the database after the app starts has no effect on the app's configuration.</span></span>

<span data-ttu-id="d52ae-115">定義 `Settings` 記錄類型實體，以將設定值儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="d52ae-115">Define a `Settings` record type entity for storing configuration values in the database.</span></span> <span data-ttu-id="d52ae-116">例如，您可以在 [*模型*] 資料夾中新增*Settings.cs*檔案：</span><span class="sxs-lookup"><span data-stu-id="d52ae-116">For example, you could add a *Settings.cs* file in your *Models* folder:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

<span data-ttu-id="d52ae-117">如需記錄類型的詳細資訊，請參閱 [c # 9 中的記錄類型](../../csharp/whats-new/csharp-9.md#record-types)。</span><span class="sxs-lookup"><span data-stu-id="d52ae-117">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="d52ae-118">新增 `EntityConfigurationContext` 以存放及存取已設定的值。</span><span class="sxs-lookup"><span data-stu-id="d52ae-118">Add an `EntityConfigurationContext` to store and access the configured values.</span></span>

<span data-ttu-id="d52ae-119">*Provider/EntityConfigurationCoNtext .cs*：</span><span class="sxs-lookup"><span data-stu-id="d52ae-119">*Providers/EntityConfigurationContext.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

<span data-ttu-id="d52ae-120">建立會實作 <xref:Microsoft.Extensions.Configuration.IConfigurationSource> 的類別。</span><span class="sxs-lookup"><span data-stu-id="d52ae-120">Create a class that implements <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.</span></span>

<span data-ttu-id="d52ae-121">*Provider/EntityConfigurationSource .cs*：</span><span class="sxs-lookup"><span data-stu-id="d52ae-121">*Providers/EntityConfigurationSource.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

<span data-ttu-id="d52ae-122">透過繼承自 <xref:Microsoft.Extensions.Configuration.ConfigurationProvider> 來建立自訂設定提供者。</span><span class="sxs-lookup"><span data-stu-id="d52ae-122">Create the custom configuration provider by inheriting from <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>.</span></span> <span data-ttu-id="d52ae-123">若資料庫是空的，設定提供者會初始化資料庫。</span><span class="sxs-lookup"><span data-stu-id="d52ae-123">The configuration provider initializes the database when it's empty.</span></span> <span data-ttu-id="d52ae-124">由於設定索引鍵不區分大小寫，因此用來初始化資料庫的字典會以不區分大小寫的比較子來建立 ([stringcomparison. OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)) 。</span><span class="sxs-lookup"><span data-stu-id="d52ae-124">Since configuration keys are case-insensitive, the dictionary used to initialize the database is created with the case-insensitive comparer ([StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).</span></span>

<span data-ttu-id="d52ae-125">*Provider/EntityConfigurationProvider .cs*：</span><span class="sxs-lookup"><span data-stu-id="d52ae-125">*Providers/EntityConfigurationProvider.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

<span data-ttu-id="d52ae-126">`AddEntityConfiguration`擴充方法允許將設定來源加入至 <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> 實例。</span><span class="sxs-lookup"><span data-stu-id="d52ae-126">An `AddEntityConfiguration` extension method permits adding the configuration source to a <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance.</span></span>

<span data-ttu-id="d52ae-127">*Extensions/ConfigurationBuilderExtensions .cs*：</span><span class="sxs-lookup"><span data-stu-id="d52ae-127">*Extensions/ConfigurationBuilderExtensions.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

<span data-ttu-id="d52ae-128">下列程式碼顯示如何在 *Program.cs* 中使用自訂 `EntityConfigurationProvider`：</span><span class="sxs-lookup"><span data-stu-id="d52ae-128">The following code shows how to use the custom `EntityConfigurationProvider` in *Program.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="21-22":::

## <a name="see-also"></a><span data-ttu-id="d52ae-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d52ae-129">See also</span></span>

- [<span data-ttu-id="d52ae-130">.NET 中的設定</span><span class="sxs-lookup"><span data-stu-id="d52ae-130">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="d52ae-131">.NET 中的設定提供者</span><span class="sxs-lookup"><span data-stu-id="d52ae-131">Configuration providers in .NET</span></span>](configuration-providers.md)
