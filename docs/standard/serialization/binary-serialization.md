---
title: 二進位序列化
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: 9df9b73a1a1347b952d76b76c9058578f5e9f401
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400635"
---
# <a name="binary-serialization"></a><span data-ttu-id="1f339-102">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="1f339-102">Binary serialization</span></span>

<span data-ttu-id="1f339-103">可定義序列化為儲存物件狀態至儲存媒體的程序。</span><span class="sxs-lookup"><span data-stu-id="1f339-103">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="1f339-104">在此程序中，物件的公用與私用欄位以及類別名稱 (包括含類別的組件)，會轉換為位元組資料流，然後寫入資料流當中。</span><span class="sxs-lookup"><span data-stu-id="1f339-104">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="1f339-105">當物件隨後還原序列化時，會建立與原始物件完全相同的複製品。</span><span class="sxs-lookup"><span data-stu-id="1f339-105">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="1f339-106">在物件導向環境中實作序列化機制時，您必須在使用簡易性與彈性之間進行許多取捨。</span><span class="sxs-lookup"><span data-stu-id="1f339-106">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="1f339-107">若您對程序擁有足夠的控制，該程序可大幅自動化。</span><span class="sxs-lookup"><span data-stu-id="1f339-107">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="1f339-108">例如，可能有簡單二進位序列化並不足夠的情況，或有特定的理由需決定類別中哪個欄位需序列化。</span><span class="sxs-lookup"><span data-stu-id="1f339-108">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="1f339-109">下列各節檢查 .NET 所提供的穩固序列化機制，並強調數種能讓您自訂程序以滿足需求的重要功能。</span><span class="sxs-lookup"><span data-stu-id="1f339-109">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="1f339-110">如果使用不同的 .NET Framework 版本序列化及還原序列化 UTF-8 或 UTF-7 編碼的物件，則不會保留該物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="1f339-110">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="1f339-111">二進位序列化允許修改物件內的私有成員，從而更改其狀態。</span><span class="sxs-lookup"><span data-stu-id="1f339-111">Binary serialization allows modifying private members inside an object and therefore changing the state of it.</span></span> <span data-ttu-id="1f339-112">因此，建議在公共 API 表面上操作的其他<xref:System.Text.Json?displayProperty=fullName>序列化框架，如 。</span><span class="sxs-lookup"><span data-stu-id="1f339-112">Because of this, other serialization frameworks, like <xref:System.Text.Json?displayProperty=fullName>, that operate on the public API surface are recommended.</span></span>

## <a name="net-core"></a><span data-ttu-id="1f339-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="1f339-113">.NET Core</span></span>

<span data-ttu-id="1f339-114">.NET Core 支援類型子集的二進位序列化。</span><span class="sxs-lookup"><span data-stu-id="1f339-114">.NET Core supports binary serialization for a subset of types.</span></span> <span data-ttu-id="1f339-115">您可以在後面的["可序列化類型"](#serializable-types)部分中查看受支援類型的清單。</span><span class="sxs-lookup"><span data-stu-id="1f339-115">You can see the list of supported types in the [Serializable types](#serializable-types) section that follows.</span></span> <span data-ttu-id="1f339-116">列出的類型保證在 .NET Framework 4.5.1 和更高版本之間以及 .NET Core 2.0 和更高版本之間可序列化。</span><span class="sxs-lookup"><span data-stu-id="1f339-116">The listed types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and between .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="1f339-117">其他 .NET 實現（如 Mono）不受官方支援，但也應正常工作。</span><span class="sxs-lookup"><span data-stu-id="1f339-117">Other .NET implementations, such as Mono, aren't officially supported but should also work.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="1f339-118">可序列化類型</span><span class="sxs-lookup"><span data-stu-id="1f339-118">Serializable types</span></span>

> [!div class="mx-tdCol2BreakAll"]
> | <span data-ttu-id="1f339-119">類型</span><span class="sxs-lookup"><span data-stu-id="1f339-119">Type</span></span> | <span data-ttu-id="1f339-120">注意</span><span class="sxs-lookup"><span data-stu-id="1f339-120">Notes</span></span> |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | <span data-ttu-id="1f339-121">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-121">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | <span data-ttu-id="1f339-122">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-122">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-123">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-123">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AggregateException?displayProperty=nameWithType> | <span data-ttu-id="1f339-124">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-124">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-125">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-125">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-126">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-126">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | <span data-ttu-id="1f339-127">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-127">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | <span data-ttu-id="1f339-128">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-128">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="1f339-129">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-129">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | <span data-ttu-id="1f339-130">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-130">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="1f339-131">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-131">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | <span data-ttu-id="1f339-132">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-132">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | <span data-ttu-id="1f339-133">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-133">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="1f339-134">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-134">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Hashtable?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Queue?displayProperty=nameWithType> | |
> | <xref:System.Collections.SortedList?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Stack?displayProperty=nameWithType> | |
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | <span data-ttu-id="1f339-135">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-135">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-136">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-136">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | <span data-ttu-id="1f339-137">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-137">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | <span data-ttu-id="1f339-138">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-138">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | <span data-ttu-id="1f339-139">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-139">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | <span data-ttu-id="1f339-140">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-140">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="1f339-141">不支援從 .NET 框架到 .NET 核心的序列化。</span><span class="sxs-lookup"><span data-stu-id="1f339-141">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | <span data-ttu-id="1f339-142">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-142">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | <span data-ttu-id="1f339-143">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-143">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | <span data-ttu-id="1f339-144">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-144">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-145">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-145">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | <span data-ttu-id="1f339-146">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-146">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="1f339-147">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-147">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="1f339-148">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-148">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | <span data-ttu-id="1f339-149">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-149">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | <span data-ttu-id="1f339-150">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-150">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DBNull?displayProperty=nameWithType> | <span data-ttu-id="1f339-151">從 .NET Core 2.0.2 和更高版本開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-151">Starting in .NET Core 2.0.2 and later versions.</span></span> |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | <span data-ttu-id="1f339-152">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-152">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | <span data-ttu-id="1f339-153">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-153">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | <span data-ttu-id="1f339-154">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-154">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | <span data-ttu-id="1f339-155">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-155">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | <span data-ttu-id="1f339-156">如果設置為`RemotingFormat``SerializationFormat.Binary`，它只能與 .NET Core 2.1 和更高版本交換。</span><span class="sxs-lookup"><span data-stu-id="1f339-156">If you set `RemotingFormat` to `SerializationFormat.Binary`, it can only be exchanged with .NET Core 2.1 and later versions.</span></span> |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | <span data-ttu-id="1f339-157">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-157">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | <span data-ttu-id="1f339-158">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-158">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | <span data-ttu-id="1f339-159">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-159">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | <span data-ttu-id="1f339-160">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-160">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | <span data-ttu-id="1f339-161">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-161">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | <span data-ttu-id="1f339-162">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-162">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | <span data-ttu-id="1f339-163">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-163">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-164">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-164">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | <span data-ttu-id="1f339-165">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-165">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-166">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-166">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | <span data-ttu-id="1f339-167">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-167">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | <span data-ttu-id="1f339-168">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-168">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | <span data-ttu-id="1f339-169">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-169">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="1f339-170">不支援從 .NET 框架到 .NET 核心的序列化</span><span class="sxs-lookup"><span data-stu-id="1f339-170">Serialization from .NET Framework to .NET Core is not supported</span></span> |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | <span data-ttu-id="1f339-171">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-171">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | <span data-ttu-id="1f339-172">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-172">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | <span data-ttu-id="1f339-173">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-173">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | <span data-ttu-id="1f339-174">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-174">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | <span data-ttu-id="1f339-175">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-175">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | <span data-ttu-id="1f339-176">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-176">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | <span data-ttu-id="1f339-177">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-177">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="1f339-178">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-178">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-179">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-179">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | <span data-ttu-id="1f339-180">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-180">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | <span data-ttu-id="1f339-181">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-181">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="1f339-182">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-182">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | <span data-ttu-id="1f339-183">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-183">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | <span data-ttu-id="1f339-184">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-184">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | <span data-ttu-id="1f339-185">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-185">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | <span data-ttu-id="1f339-186">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-186">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | <span data-ttu-id="1f339-187">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-187">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-188">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-188">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | <span data-ttu-id="1f339-189">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-189">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | <span data-ttu-id="1f339-190">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-190">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="1f339-191">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-191">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-192">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-192">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | <span data-ttu-id="1f339-193">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-193">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | <span data-ttu-id="1f339-194">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-194">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-195">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-195">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | <span data-ttu-id="1f339-196">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-196">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | <span data-ttu-id="1f339-197">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-197">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | <span data-ttu-id="1f339-198">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-198">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-199">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-199">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | <span data-ttu-id="1f339-200">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-200">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-201">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-201">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | <span data-ttu-id="1f339-202">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-202">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="1f339-203">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-203">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | <span data-ttu-id="1f339-204">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-204">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="1f339-205">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-205">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | <span data-ttu-id="1f339-206">從 .NET 核心 2.0.6 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-206">Starting in .NET Core 2.0.6.</span></span> |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | <span data-ttu-id="1f339-207">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-207">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | <span data-ttu-id="1f339-208">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-208">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.FormatException?displayProperty=nameWithType> | <span data-ttu-id="1f339-209">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-209">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="1f339-210">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-210">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | <span data-ttu-id="1f339-211">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-211">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="1f339-212">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-212">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | <span data-ttu-id="1f339-213">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-213">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | <span data-ttu-id="1f339-214">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-214">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | <span data-ttu-id="1f339-215">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-215">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="1f339-216">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-216">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | <span data-ttu-id="1f339-217">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-217">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | <span data-ttu-id="1f339-218">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-218">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | <span data-ttu-id="1f339-219">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-219">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | <span data-ttu-id="1f339-220">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-220">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | <span data-ttu-id="1f339-221">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-221">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | <span data-ttu-id="1f339-222">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-222">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | <span data-ttu-id="1f339-223">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-223">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | <span data-ttu-id="1f339-224">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-224">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | <span data-ttu-id="1f339-225">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-225">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-226">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-226">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | <span data-ttu-id="1f339-227">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-227">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | <span data-ttu-id="1f339-228">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-228">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | <span data-ttu-id="1f339-229">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-229">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | <span data-ttu-id="1f339-230">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-230">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | <span data-ttu-id="1f339-231">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-231">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | <span data-ttu-id="1f339-232">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-232">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | <span data-ttu-id="1f339-233">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-233">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-234">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-234">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | <span data-ttu-id="1f339-235">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-235">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | <span data-ttu-id="1f339-236">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-236">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | <span data-ttu-id="1f339-237">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-237">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | <span data-ttu-id="1f339-238">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-238">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | <span data-ttu-id="1f339-239">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-239">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-240">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-240">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | <span data-ttu-id="1f339-241">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-241">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-242">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-242">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | <span data-ttu-id="1f339-243">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-243">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | <span data-ttu-id="1f339-244">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-244">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | <span data-ttu-id="1f339-245">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-245">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | <span data-ttu-id="1f339-246">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-246">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-247">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-247">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-248">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-248">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | <span data-ttu-id="1f339-249">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-249">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-250">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-250">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | <span data-ttu-id="1f339-251">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-251">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | <span data-ttu-id="1f339-252">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-252">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.OverflowException?displayProperty=nameWithType> | <span data-ttu-id="1f339-253">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-253">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-254">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-254">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.RankException?displayProperty=nameWithType> | <span data-ttu-id="1f339-255">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-255">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | <span data-ttu-id="1f339-256">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-256">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | <span data-ttu-id="1f339-257">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-257">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | <span data-ttu-id="1f339-258">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-258">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="1f339-259">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-259">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="1f339-260">不支援從 .NET 框架到 .NET 核心的序列化。</span><span class="sxs-lookup"><span data-stu-id="1f339-260">Serialization from .NET Framework to .NET Core is not supported.</span></span> |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | <span data-ttu-id="1f339-261">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-261">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-262">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-262">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | <span data-ttu-id="1f339-263">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-263">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | <span data-ttu-id="1f339-264">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-264">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | <span data-ttu-id="1f339-265">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-265">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-266">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-266">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | <span data-ttu-id="1f339-267">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-267">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | <span data-ttu-id="1f339-268">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-268">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | <span data-ttu-id="1f339-269">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-269">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | <span data-ttu-id="1f339-270">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-270">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | <span data-ttu-id="1f339-271">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-271">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | <span data-ttu-id="1f339-272">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-272">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | <span data-ttu-id="1f339-273">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-273">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | <span data-ttu-id="1f339-274">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-274">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | <span data-ttu-id="1f339-275">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-275">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-276">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-276">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | <span data-ttu-id="1f339-277">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-277">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-278">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-278">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | <span data-ttu-id="1f339-279">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-279">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | <span data-ttu-id="1f339-280">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-280">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-281">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-281">Starting in .NET Core 2.0.4.</span></span> |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | <span data-ttu-id="1f339-282">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-282">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | <span data-ttu-id="1f339-283">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-283">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | <span data-ttu-id="1f339-284">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-284">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-285">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-285">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | <span data-ttu-id="1f339-286">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-286">Starting in .NET Core 2.0.4.</span></span><br/><span data-ttu-id="1f339-287">有限的序列化資料。</span><span class="sxs-lookup"><span data-stu-id="1f339-287">Limited serialization data.</span></span> |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-288">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-288">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | <span data-ttu-id="1f339-289">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-289">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="1f339-290">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-290">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | <span data-ttu-id="1f339-291">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-291">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | <span data-ttu-id="1f339-292">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-292">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="1f339-293">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-293">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | <span data-ttu-id="1f339-294">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-294">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | <span data-ttu-id="1f339-295">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-295">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | <span data-ttu-id="1f339-296">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-296">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | <span data-ttu-id="1f339-297">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-297">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | <span data-ttu-id="1f339-298">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-298">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | <span data-ttu-id="1f339-299">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-299">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | <span data-ttu-id="1f339-300">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-300">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | <span data-ttu-id="1f339-301">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-301">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | <span data-ttu-id="1f339-302">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-302">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | <span data-ttu-id="1f339-303">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-303">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-304">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-304">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | <span data-ttu-id="1f339-305">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-305">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | <span data-ttu-id="1f339-306">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-306">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-307">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-307">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | <span data-ttu-id="1f339-308">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-308">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | <span data-ttu-id="1f339-309">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-309">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-310">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-310">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | <span data-ttu-id="1f339-311">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-311">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | <span data-ttu-id="1f339-312">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-312">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-313">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-313">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | <span data-ttu-id="1f339-314">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-314">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | <span data-ttu-id="1f339-315">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-315">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-316">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-316">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | <span data-ttu-id="1f339-317">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-317">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | <span data-ttu-id="1f339-318">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-318">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | <span data-ttu-id="1f339-319">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-319">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | <span data-ttu-id="1f339-320">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-320">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | <span data-ttu-id="1f339-321">在 .NET 框架 4.7 和早期版本中不可序列化。</span><span class="sxs-lookup"><span data-stu-id="1f339-321">Not serializable in .NET Framework 4.7 and earlier versions.</span></span> |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | <span data-ttu-id="1f339-322">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-322">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | <span data-ttu-id="1f339-323">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-323">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | <span data-ttu-id="1f339-324">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-324">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | <span data-ttu-id="1f339-325">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-325">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | <span data-ttu-id="1f339-326">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-326">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | <span data-ttu-id="1f339-327">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-327">Starting in .NET Core 2.0.4.</span></span> |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | <span data-ttu-id="1f339-328">從 .NET 核心 2.0.4 開始。</span><span class="sxs-lookup"><span data-stu-id="1f339-328">Starting in .NET Core 2.0.4.</span></span> |

## <a name="see-also"></a><span data-ttu-id="1f339-329">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f339-329">See also</span></span>

- <xref:System.Runtime.Serialization>\
<span data-ttu-id="1f339-330">包含類別，可以用來序列化和還原序列化物件。</span><span class="sxs-lookup"><span data-stu-id="1f339-330">Contains classes that can be used for serializing and deserializing objects.</span></span>

- <span data-ttu-id="1f339-331">[XML 和 SOAP 序列化](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="1f339-331">[XML and SOAP Serialization](../../../docs/standard/serialization/xml-and-soap-serialization.md)</span></span>\
<span data-ttu-id="1f339-332">說明 Common Language Runtime 中所含的 XML 序列化機制。</span><span class="sxs-lookup"><span data-stu-id="1f339-332">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>

- <span data-ttu-id="1f339-333">[安全性和序列化](../../../docs/framework/misc/security-and-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="1f339-333">[Security and Serialization](../../../docs/framework/misc/security-and-serialization.md)</span></span>\
<span data-ttu-id="1f339-334">說明在撰寫執行序列化的程式碼時要遵循的安全程式碼撰寫方針。</span><span class="sxs-lookup"><span data-stu-id="1f339-334">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>

- <span data-ttu-id="1f339-335">[.NET 遠端處理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1f339-335">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>\
<span data-ttu-id="1f339-336">描述從 .NET 遠端通訊框架開始的各種方法。</span><span class="sxs-lookup"><span data-stu-id="1f339-336">Describes the various methods Starting in .NET Framework for remote communications.</span></span>

- <span data-ttu-id="1f339-337">[使用ASP.NET和XML Web服務用戶端創建的 XML Web 服務](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1f339-337">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>\
<span data-ttu-id="1f339-338">描述並解釋如何使用ASP.NET創建的 XML Web 服務。</span><span class="sxs-lookup"><span data-stu-id="1f339-338">Articles that describe and explain how to program XML Web services created using ASP.NET.</span></span>
