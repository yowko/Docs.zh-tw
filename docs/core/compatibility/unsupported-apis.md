---
title: .NET 內核上不受支援的 API
titleSuffix: ''
description: 瞭解在 .NET 核心上始終引發異常的 .NET 框架中的哪些 API。
ms.date: 12/23/2019
ms.openlocfilehash: bd3516d9480ef42b6ea89825ba64867a3ca104e3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242942"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="4f9f6-103">始終在 .NET 內核上引發異常的 API</span><span class="sxs-lookup"><span data-stu-id="4f9f6-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="4f9f6-104">以下 API 將始終<xref:System.PlatformNotSupportedException>在所有 平台或平臺子集上引發 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="4f9f6-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="4f9f6-105">本文按命名空間組織受影響的 API 成員。</span><span class="sxs-lookup"><span data-stu-id="4f9f6-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="4f9f6-106">本文正在進行中。</span><span class="sxs-lookup"><span data-stu-id="4f9f6-106">This article is a work-in-progress.</span></span> <span data-ttu-id="4f9f6-107">它不是在 .NET Core 上引發異常的完整 API 清單。</span><span class="sxs-lookup"><span data-stu-id="4f9f6-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="4f9f6-108">本文不包括在 .NET Core 上拋出的二進位序列化的顯式介面實現。</span><span class="sxs-lookup"><span data-stu-id="4f9f6-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="4f9f6-109">有關詳細資訊,請參閱[.NET 核心 中的二進位序列化](../../standard/serialization/binary-serialization.md#net-core)。</span><span class="sxs-lookup"><span data-stu-id="4f9f6-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="4f9f6-110">系統</span><span class="sxs-lookup"><span data-stu-id="4f9f6-110">System</span></span>

| <span data-ttu-id="4f9f6-111">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-111">Member</span></span> | <span data-ttu-id="4f9f6-112">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-113">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-114">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-115">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-116">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-117">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-118">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-119">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-120">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-121">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-122">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="4f9f6-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="4f9f6-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="4f9f6-124">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-124">Member</span></span> | <span data-ttu-id="4f9f6-125">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-126">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-127">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-128">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="4f9f6-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="4f9f6-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="4f9f6-130">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-130">Member</span></span> | <span data-ttu-id="4f9f6-131">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-132">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-133">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-134">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="4f9f6-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="4f9f6-135">System.Configuration</span></span>

| <span data-ttu-id="4f9f6-136">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-136">Member</span></span> | <span data-ttu-id="4f9f6-137">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="4f9f6-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(所有成員)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="4f9f6-139">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="4f9f6-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="4f9f6-140">System.Console</span></span>

| <span data-ttu-id="4f9f6-141">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-141">Member</span></span> | <span data-ttu-id="4f9f6-142">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-143">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-143">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-145">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-145">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-147">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-147">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-149">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-149">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(僅取得)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="4f9f6-151">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-152">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-153">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-154">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-154">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-155"><xref:System.Console.Title?displayProperty=nameWithType>(僅取得)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="4f9f6-156">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-156">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-158">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-158">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-160">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-160">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-162">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-162">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-164">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="4f9f6-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="4f9f6-165">System.Data.Common</span></span>

| <span data-ttu-id="4f9f6-166">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-166">Member</span></span> | <span data-ttu-id="4f9f6-167">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="4f9f6-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>( 投<xref:System.NotSupportedException>擲 )</span><span class="sxs-lookup"><span data-stu-id="4f9f6-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="4f9f6-169">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="4f9f6-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="4f9f6-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="4f9f6-171">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-171">Member</span></span> | <span data-ttu-id="4f9f6-172">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="4f9f6-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-174">Linux</span><span class="sxs-lookup"><span data-stu-id="4f9f6-174">Linux</span></span> |
| <span data-ttu-id="4f9f6-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-176">Linux</span><span class="sxs-lookup"><span data-stu-id="4f9f6-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-177">macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-178">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-179">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-180">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-181">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-182">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-183">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-183">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-185">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-185">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(僅取得)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="4f9f6-187">macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-187">macOS</span></span> |
| <span data-ttu-id="4f9f6-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-189">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="4f9f6-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="4f9f6-190">System.IO</span></span>

| <span data-ttu-id="4f9f6-191">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-191">Member</span></span> | <span data-ttu-id="4f9f6-192">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-193">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-194">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="4f9f6-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="4f9f6-195">System.IO.Pipes</span></span>

| <span data-ttu-id="4f9f6-196">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-196">Member</span></span> | <span data-ttu-id="4f9f6-197">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-198">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-199">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-200">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-201">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-201">Linux and macOS</span></span> |
| <span data-ttu-id="4f9f6-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-203">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-204">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="4f9f6-205">系統.媒體</span><span class="sxs-lookup"><span data-stu-id="4f9f6-205">System.Media</span></span>

| <span data-ttu-id="4f9f6-206">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-206">Member</span></span> | <span data-ttu-id="4f9f6-207">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-208">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="4f9f6-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="4f9f6-209">System.Net</span></span>

| <span data-ttu-id="4f9f6-210">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-210">Member</span></span> | <span data-ttu-id="4f9f6-211">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-212">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-213">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-214">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-215">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-216">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-217">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-218">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-219">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-220">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-221">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-222">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-223">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-224">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-225">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-226">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-227">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-228">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="4f9f6-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="4f9f6-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="4f9f6-230">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-230">Member</span></span> | <span data-ttu-id="4f9f6-231">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-232">視窗 (UWP)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="4f9f6-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="4f9f6-233">System.Net.Sockets</span></span>

| <span data-ttu-id="4f9f6-234">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-234">Member</span></span> | <span data-ttu-id="4f9f6-235">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="4f9f6-236">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-237">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="4f9f6-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="4f9f6-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="4f9f6-239">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-239">Member</span></span> | <span data-ttu-id="4f9f6-240">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-241">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="4f9f6-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="4f9f6-242">System.Reflection</span></span>

| <span data-ttu-id="4f9f6-243">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-243">Member</span></span> | <span data-ttu-id="4f9f6-244">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-245">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-246">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-247">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-248">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="4f9f6-249">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-250">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-251">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="4f9f6-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="4f9f6-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="4f9f6-253">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-253">Member</span></span> | <span data-ttu-id="4f9f6-254">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-255">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="4f9f6-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="4f9f6-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="4f9f6-257">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-257">Member</span></span> | <span data-ttu-id="4f9f6-258">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-259">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-260">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-261">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-262">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-263">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-264">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-265">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="4f9f6-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="4f9f6-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="4f9f6-267">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-267">Member</span></span> | <span data-ttu-id="4f9f6-268">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-269">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="4f9f6-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="4f9f6-270">System.Security</span></span>

| <span data-ttu-id="4f9f6-271">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-271">Member</span></span> | <span data-ttu-id="4f9f6-272">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-273">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-274">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-275">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-276">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-277">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-278">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-279">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-280">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-281">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-282">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-283">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-284">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-285">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-286">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="4f9f6-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="4f9f6-287">System.Security.Claims</span></span>

| <span data-ttu-id="4f9f6-288">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-288">Member</span></span> | <span data-ttu-id="4f9f6-289">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="4f9f6-290">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-291">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="4f9f6-292">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-293">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-294">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="4f9f6-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="4f9f6-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="4f9f6-296">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-296">Member</span></span> | <span data-ttu-id="4f9f6-297">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-298">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="4f9f6-299">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-300">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-301">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-302">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-303">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-304">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-305">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-306">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-307">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-308">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-309">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-310">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-311">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-312">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-313">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-314">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-315">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-316">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-317">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-318">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-319">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-320">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-321">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4f9f6-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-322">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-323">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-324">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-325">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="4f9f6-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="4f9f6-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="4f9f6-327">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-327">Member</span></span> | <span data-ttu-id="4f9f6-328">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="4f9f6-329">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-330">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-331">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="4f9f6-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="4f9f6-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="4f9f6-333">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-333">Member</span></span> | <span data-ttu-id="4f9f6-334">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-335">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-336">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-337">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-337">All</span></span> |
| <span data-ttu-id="4f9f6-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(僅限設定)</span><span class="sxs-lookup"><span data-stu-id="4f9f6-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4f9f6-339">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="4f9f6-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="4f9f6-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="4f9f6-341">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-341">Member</span></span> | <span data-ttu-id="4f9f6-342">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-343">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="4f9f6-344">系統.安全.政策</span><span class="sxs-lookup"><span data-stu-id="4f9f6-344">System.Security.Policy</span></span>

| <span data-ttu-id="4f9f6-345">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-345">Member</span></span> | <span data-ttu-id="4f9f6-346">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-347">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="4f9f6-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="4f9f6-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="4f9f6-349">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-349">Member</span></span> | <span data-ttu-id="4f9f6-350">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4f9f6-351">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="4f9f6-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="4f9f6-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="4f9f6-353">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-353">Member</span></span> | <span data-ttu-id="4f9f6-354">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-355">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="4f9f6-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="4f9f6-356">System.Threading</span></span>

| <span data-ttu-id="4f9f6-357">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-357">Member</span></span> | <span data-ttu-id="4f9f6-358">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-359">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-360">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-361">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-362">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-363">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-364">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="4f9f6-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="4f9f6-365">System.Xml</span></span>

| <span data-ttu-id="4f9f6-366">member</span><span class="sxs-lookup"><span data-stu-id="4f9f6-366">Member</span></span> | <span data-ttu-id="4f9f6-367">投擲的平臺</span><span class="sxs-lookup"><span data-stu-id="4f9f6-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-368">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-369">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="4f9f6-370">全部</span><span class="sxs-lookup"><span data-stu-id="4f9f6-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="4f9f6-371">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f9f6-371">See also</span></span>

- [<span data-ttu-id="4f9f6-372">從 .NET 框架移轉到 .NET 核心的中斷變更</span><span class="sxs-lookup"><span data-stu-id="4f9f6-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="4f9f6-373">.NET Core 中的二進位序列化</span><span class="sxs-lookup"><span data-stu-id="4f9f6-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="4f9f6-374">.NET 可移植性分析儀</span><span class="sxs-lookup"><span data-stu-id="4f9f6-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
