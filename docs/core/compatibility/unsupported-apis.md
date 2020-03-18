---
title: .NET 內核上不受支援的 API
titleSuffix: ''
description: 瞭解在 .NET 核心上始終引發異常的 .NET 框架中的哪些 API。
ms.date: 12/23/2019
ms.openlocfilehash: c4b94321d30cacd90d5c2ee23c258681683a6faa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092963"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="8aff1-103">始終在 .NET 內核上引發異常的 API</span><span class="sxs-lookup"><span data-stu-id="8aff1-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="8aff1-104">以下 API 將始終在所有<xref:System.PlatformNotSupportedException>平臺或平臺子集上引發 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="8aff1-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="8aff1-105">本文按命名空間組織受影響的 API 成員。</span><span class="sxs-lookup"><span data-stu-id="8aff1-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="8aff1-106">本文正在進行中。</span><span class="sxs-lookup"><span data-stu-id="8aff1-106">This article is a work-in-progress.</span></span> <span data-ttu-id="8aff1-107">它不是在 .NET Core 上引發異常的完整 API 清單。</span><span class="sxs-lookup"><span data-stu-id="8aff1-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="8aff1-108">本文不包括在 .NET Core 上拋出的二進位序列化的明確介面實作。</span><span class="sxs-lookup"><span data-stu-id="8aff1-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="8aff1-109">有關詳細資訊，請參閱[.NET 核心 中的二進位序列化](../../standard/serialization/binary-serialization.md#net-core)。</span><span class="sxs-lookup"><span data-stu-id="8aff1-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="8aff1-110">系統</span><span class="sxs-lookup"><span data-stu-id="8aff1-110">System</span></span>

| <span data-ttu-id="8aff1-111">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-111">Member</span></span> | <span data-ttu-id="8aff1-112">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-113">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-114">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="8aff1-115">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="8aff1-116">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-117">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="8aff1-118">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="8aff1-119">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="8aff1-120">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-121">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-122">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="8aff1-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="8aff1-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="8aff1-124">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-124">Member</span></span> | <span data-ttu-id="8aff1-125">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-126">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-127">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-128">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="8aff1-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="8aff1-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="8aff1-130">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-130">Member</span></span> | <span data-ttu-id="8aff1-131">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-132">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-133">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-134">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="8aff1-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="8aff1-135">System.Configuration</span></span>

| <span data-ttu-id="8aff1-136">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-136">Member</span></span> | <span data-ttu-id="8aff1-137">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="8aff1-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>（所有成員）</span><span class="sxs-lookup"><span data-stu-id="8aff1-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="8aff1-139">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="8aff1-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="8aff1-140">System.Console</span></span>

| <span data-ttu-id="8aff1-141">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-141">Member</span></span> | <span data-ttu-id="8aff1-142">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="8aff1-143">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-143">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-145">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-145">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-147">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-147">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-149">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-149">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>（僅獲取）</span><span class="sxs-lookup"><span data-stu-id="8aff1-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="8aff1-151">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-152">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-153">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-154">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-154">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-155"><xref:System.Console.Title?displayProperty=nameWithType>（僅獲取）</span><span class="sxs-lookup"><span data-stu-id="8aff1-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="8aff1-156">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-156">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-158">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-158">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-160">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-160">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-162">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-162">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-164">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="8aff1-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="8aff1-165">System.Data.Common</span></span>

| <span data-ttu-id="8aff1-166">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-166">Member</span></span> | <span data-ttu-id="8aff1-167">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="8aff1-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>（投擲<xref:System.NotSupportedException>）</span><span class="sxs-lookup"><span data-stu-id="8aff1-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="8aff1-169">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="8aff1-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="8aff1-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="8aff1-171">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-171">Member</span></span> | <span data-ttu-id="8aff1-172">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="8aff1-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-174">Linux</span><span class="sxs-lookup"><span data-stu-id="8aff1-174">Linux</span></span> |
| <span data-ttu-id="8aff1-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-176">Linux</span><span class="sxs-lookup"><span data-stu-id="8aff1-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="8aff1-177">macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="8aff1-178">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-179">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="8aff1-180">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="8aff1-181">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="8aff1-182">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="8aff1-183">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-183">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-185">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-185">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>（僅獲取）</span><span class="sxs-lookup"><span data-stu-id="8aff1-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="8aff1-187">macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-187">macOS</span></span> |
| <span data-ttu-id="8aff1-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-189">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="8aff1-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="8aff1-190">System.IO</span></span>

| <span data-ttu-id="8aff1-191">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-191">Member</span></span> | <span data-ttu-id="8aff1-192">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-193">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-194">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="8aff1-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="8aff1-195">System.IO.Pipes</span></span>

| <span data-ttu-id="8aff1-196">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-196">Member</span></span> | <span data-ttu-id="8aff1-197">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="8aff1-198">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="8aff1-199">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="8aff1-200">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="8aff1-201">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-201">Linux and macOS</span></span> |
| <span data-ttu-id="8aff1-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-203">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="8aff1-204">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="8aff1-205">系統.媒體</span><span class="sxs-lookup"><span data-stu-id="8aff1-205">System.Media</span></span>

| <span data-ttu-id="8aff1-206">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-206">Member</span></span> | <span data-ttu-id="8aff1-207">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-208">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="8aff1-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="8aff1-209">System.Net</span></span>

| <span data-ttu-id="8aff1-210">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-210">Member</span></span> | <span data-ttu-id="8aff1-211">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-212">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-213">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-214">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-215">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-216">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-217">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-218">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-219">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-220">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-221">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-222">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="8aff1-223">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-224">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-225">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-226">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-227">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-228">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="8aff1-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="8aff1-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="8aff1-230">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-230">Member</span></span> | <span data-ttu-id="8aff1-231">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-232">視窗 （UWP）</span><span class="sxs-lookup"><span data-stu-id="8aff1-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="8aff1-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="8aff1-233">System.Net.Sockets</span></span>

| <span data-ttu-id="8aff1-234">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-234">Member</span></span> | <span data-ttu-id="8aff1-235">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-236">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-237">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="8aff1-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="8aff1-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="8aff1-239">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-239">Member</span></span> | <span data-ttu-id="8aff1-240">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="8aff1-241">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="8aff1-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="8aff1-242">System.Reflection</span></span>

| <span data-ttu-id="8aff1-243">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-243">Member</span></span> | <span data-ttu-id="8aff1-244">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-245">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-246">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-247">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-248">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-249">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-250">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="8aff1-251">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="8aff1-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="8aff1-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="8aff1-253">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-253">Member</span></span> | <span data-ttu-id="8aff1-254">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="8aff1-255">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="8aff1-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="8aff1-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="8aff1-257">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-257">Member</span></span> | <span data-ttu-id="8aff1-258">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-259">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="8aff1-260">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-261">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-262">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-263">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-264">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-265">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="8aff1-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="8aff1-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="8aff1-267">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-267">Member</span></span> | <span data-ttu-id="8aff1-268">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="8aff1-269">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="8aff1-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="8aff1-270">System.Security</span></span>

| <span data-ttu-id="8aff1-271">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-271">Member</span></span> | <span data-ttu-id="8aff1-272">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="8aff1-273">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="8aff1-274">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-275">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="8aff1-276">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="8aff1-277">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="8aff1-278">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="8aff1-279">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="8aff1-280">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="8aff1-281">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="8aff1-282">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="8aff1-283">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-284">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="8aff1-285">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="8aff1-286">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="8aff1-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="8aff1-287">System.Security.Claims</span></span>

| <span data-ttu-id="8aff1-288">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-288">Member</span></span> | <span data-ttu-id="8aff1-289">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="8aff1-290">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-291">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-292">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-293">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-294">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="8aff1-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="8aff1-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="8aff1-296">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-296">Member</span></span> | <span data-ttu-id="8aff1-297">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-298">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-299">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="8aff1-300">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="8aff1-301">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="8aff1-302">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="8aff1-303">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="8aff1-304">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="8aff1-305">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="8aff1-306">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="8aff1-307">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="8aff1-308">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="8aff1-309">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="8aff1-310">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="8aff1-311">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="8aff1-312">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="8aff1-313">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-314">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-315">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-316">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-317">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="8aff1-318">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-319">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-320">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-321">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="8aff1-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-322">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-323">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="8aff1-324">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-325">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="8aff1-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="8aff1-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="8aff1-327">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-327">Member</span></span> | <span data-ttu-id="8aff1-328">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-329">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-330">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="8aff1-331">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="8aff1-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="8aff1-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="8aff1-333">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-333">Member</span></span> | <span data-ttu-id="8aff1-334">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-335">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-336">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-337">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-337">All</span></span> |
| <span data-ttu-id="8aff1-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>（僅限設置）</span><span class="sxs-lookup"><span data-stu-id="8aff1-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="8aff1-339">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="8aff1-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="8aff1-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="8aff1-341">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-341">Member</span></span> | <span data-ttu-id="8aff1-342">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-343">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="8aff1-344">系統.安全.政策</span><span class="sxs-lookup"><span data-stu-id="8aff1-344">System.Security.Policy</span></span>

| <span data-ttu-id="8aff1-345">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-345">Member</span></span> | <span data-ttu-id="8aff1-346">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-347">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="8aff1-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="8aff1-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="8aff1-349">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-349">Member</span></span> | <span data-ttu-id="8aff1-350">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-351">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="8aff1-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="8aff1-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="8aff1-353">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-353">Member</span></span> | <span data-ttu-id="8aff1-354">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-355">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="8aff1-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="8aff1-356">System.Threading</span></span>

| <span data-ttu-id="8aff1-357">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-357">Member</span></span> | <span data-ttu-id="8aff1-358">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-359">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-360">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="8aff1-361">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="8aff1-362">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="8aff1-363">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="8aff1-364">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="8aff1-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="8aff1-365">System.Xml</span></span>

| <span data-ttu-id="8aff1-366">member</span><span class="sxs-lookup"><span data-stu-id="8aff1-366">Member</span></span> | <span data-ttu-id="8aff1-367">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="8aff1-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-368">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-369">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="8aff1-370">全部</span><span class="sxs-lookup"><span data-stu-id="8aff1-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="8aff1-371">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8aff1-371">See also</span></span>

- [<span data-ttu-id="8aff1-372">從 .NET 框架遷移到 .NET 核心的中斷更改</span><span class="sxs-lookup"><span data-stu-id="8aff1-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="8aff1-373">.NET Core 中的二進位序列化</span><span class="sxs-lookup"><span data-stu-id="8aff1-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="8aff1-374">.NET 可攜性分析儀</span><span class="sxs-lookup"><span data-stu-id="8aff1-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
