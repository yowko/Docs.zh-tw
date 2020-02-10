---
title: .NET Core 上不支援的 Api
titleSuffix: ''
description: 瞭解 .NET Framework 中一律會在 .NET Core 上擲回例外狀況的 Api。
ms.date: 12/23/2019
ms.openlocfilehash: c4b94321d30cacd90d5c2ee23c258681683a6faa
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092963"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="cf122-103">在 .NET Core 上一律會擲回例外狀況的 Api</span><span class="sxs-lookup"><span data-stu-id="cf122-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="cf122-104">下列 Api 一律會在所有或部分平臺的 .NET Core 上擲回 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="cf122-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="cf122-105">本文會依照命名空間來組織受影響的 API 成員。</span><span class="sxs-lookup"><span data-stu-id="cf122-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="cf122-106">這篇文章是一個進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="cf122-106">This article is a work-in-progress.</span></span> <span data-ttu-id="cf122-107">這不是在 .NET Core 上擲回例外狀況的完整 Api 清單。</span><span class="sxs-lookup"><span data-stu-id="cf122-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="cf122-108">本文不包含在 .NET Core 上擲回之二進位序列化的明確介面執行。</span><span class="sxs-lookup"><span data-stu-id="cf122-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="cf122-109">如需詳細資訊，請參閱[.Net Core 中的二進位序列化](../../standard/serialization/binary-serialization.md#net-core)。</span><span class="sxs-lookup"><span data-stu-id="cf122-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="cf122-110">系統</span><span class="sxs-lookup"><span data-stu-id="cf122-110">System</span></span>

| <span data-ttu-id="cf122-111">member</span><span class="sxs-lookup"><span data-stu-id="cf122-111">Member</span></span> | <span data-ttu-id="cf122-112">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-113">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="cf122-114">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="cf122-115">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="cf122-116">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-117">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="cf122-118">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="cf122-119">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="cf122-120">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-121">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="cf122-122">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="cf122-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="cf122-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="cf122-124">member</span><span class="sxs-lookup"><span data-stu-id="cf122-124">Member</span></span> | <span data-ttu-id="cf122-125">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-126">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-127">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-128">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="cf122-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="cf122-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="cf122-130">member</span><span class="sxs-lookup"><span data-stu-id="cf122-130">Member</span></span> | <span data-ttu-id="cf122-131">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-132">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-133">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="cf122-134">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="cf122-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="cf122-135">System.Configuration</span></span>

| <span data-ttu-id="cf122-136">member</span><span class="sxs-lookup"><span data-stu-id="cf122-136">Member</span></span> | <span data-ttu-id="cf122-137">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="cf122-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> （所有成員）</span><span class="sxs-lookup"><span data-stu-id="cf122-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="cf122-139">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="cf122-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="cf122-140">System.Console</span></span>

| <span data-ttu-id="cf122-141">member</span><span class="sxs-lookup"><span data-stu-id="cf122-141">Member</span></span> | <span data-ttu-id="cf122-142">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="cf122-143">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-143">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-145">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-145">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-147">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-147">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-149">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-149">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> （僅限取得）</span><span class="sxs-lookup"><span data-stu-id="cf122-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="cf122-151">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-152">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-153">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-154">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-154">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-155"><xref:System.Console.Title?displayProperty=nameWithType> （僅限取得）</span><span class="sxs-lookup"><span data-stu-id="cf122-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="cf122-156">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-156">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-158">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-158">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-160">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-160">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-162">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-162">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-164">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="cf122-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="cf122-165">System.Data.Common</span></span>

| <span data-ttu-id="cf122-166">member</span><span class="sxs-lookup"><span data-stu-id="cf122-166">Member</span></span> | <span data-ttu-id="cf122-167">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="cf122-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> （擲回 <xref:System.NotSupportedException>）</span><span class="sxs-lookup"><span data-stu-id="cf122-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="cf122-169">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="cf122-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="cf122-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="cf122-171">member</span><span class="sxs-lookup"><span data-stu-id="cf122-171">Member</span></span> | <span data-ttu-id="cf122-172">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="cf122-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-174">Linux</span><span class="sxs-lookup"><span data-stu-id="cf122-174">Linux</span></span> |
| <span data-ttu-id="cf122-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-176">Linux</span><span class="sxs-lookup"><span data-stu-id="cf122-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="cf122-177">macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="cf122-178">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-179">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="cf122-180">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="cf122-181">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="cf122-182">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="cf122-183">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-183">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-185">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-185">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> （僅限取得）</span><span class="sxs-lookup"><span data-stu-id="cf122-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="cf122-187">macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-187">macOS</span></span> |
| <span data-ttu-id="cf122-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-189">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="cf122-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="cf122-190">System.IO</span></span>

| <span data-ttu-id="cf122-191">member</span><span class="sxs-lookup"><span data-stu-id="cf122-191">Member</span></span> | <span data-ttu-id="cf122-192">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-193">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-194">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="cf122-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="cf122-195">System.IO.Pipes</span></span>

| <span data-ttu-id="cf122-196">member</span><span class="sxs-lookup"><span data-stu-id="cf122-196">Member</span></span> | <span data-ttu-id="cf122-197">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="cf122-198">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="cf122-199">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="cf122-200">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="cf122-201">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-201">Linux and macOS</span></span> |
| <span data-ttu-id="cf122-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-203">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="cf122-204">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="cf122-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="cf122-205">System.Media</span></span>

| <span data-ttu-id="cf122-206">member</span><span class="sxs-lookup"><span data-stu-id="cf122-206">Member</span></span> | <span data-ttu-id="cf122-207">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-208">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="cf122-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="cf122-209">System.Net</span></span>

| <span data-ttu-id="cf122-210">member</span><span class="sxs-lookup"><span data-stu-id="cf122-210">Member</span></span> | <span data-ttu-id="cf122-211">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="cf122-212">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="cf122-213">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-214">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-215">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-216">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-217">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-218">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-219">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-220">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-221">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-222">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="cf122-223">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-224">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-225">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-226">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-227">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-228">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="cf122-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="cf122-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="cf122-230">member</span><span class="sxs-lookup"><span data-stu-id="cf122-230">Member</span></span> | <span data-ttu-id="cf122-231">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-232">Windows （UWP）</span><span class="sxs-lookup"><span data-stu-id="cf122-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="cf122-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="cf122-233">System.Net.Sockets</span></span>

| <span data-ttu-id="cf122-234">member</span><span class="sxs-lookup"><span data-stu-id="cf122-234">Member</span></span> | <span data-ttu-id="cf122-235">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)?displayProperty=nameWithType> | <span data-ttu-id="cf122-236">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="cf122-237">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="cf122-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="cf122-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="cf122-239">member</span><span class="sxs-lookup"><span data-stu-id="cf122-239">Member</span></span> | <span data-ttu-id="cf122-240">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="cf122-241">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="cf122-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="cf122-242">System.Reflection</span></span>

| <span data-ttu-id="cf122-243">member</span><span class="sxs-lookup"><span data-stu-id="cf122-243">Member</span></span> | <span data-ttu-id="cf122-244">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-245">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cf122-246">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-247">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="cf122-248">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cf122-249">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-250">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="cf122-251">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="cf122-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="cf122-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="cf122-253">member</span><span class="sxs-lookup"><span data-stu-id="cf122-253">Member</span></span> | <span data-ttu-id="cf122-254">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="cf122-255">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="cf122-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="cf122-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="cf122-257">member</span><span class="sxs-lookup"><span data-stu-id="cf122-257">Member</span></span> | <span data-ttu-id="cf122-258">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="cf122-259">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="cf122-260">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="cf122-261">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="cf122-262">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cf122-263">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="cf122-264">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="cf122-265">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="cf122-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="cf122-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="cf122-267">member</span><span class="sxs-lookup"><span data-stu-id="cf122-267">Member</span></span> | <span data-ttu-id="cf122-268">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="cf122-269">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="cf122-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="cf122-270">System.Security</span></span>

| <span data-ttu-id="cf122-271">member</span><span class="sxs-lookup"><span data-stu-id="cf122-271">Member</span></span> | <span data-ttu-id="cf122-272">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="cf122-273">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="cf122-274">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="cf122-275">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="cf122-276">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="cf122-277">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="cf122-278">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="cf122-279">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="cf122-280">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="cf122-281">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="cf122-282">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="cf122-283">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="cf122-284">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="cf122-285">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="cf122-286">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="cf122-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="cf122-287">System.Security.Claims</span></span>

| <span data-ttu-id="cf122-288">member</span><span class="sxs-lookup"><span data-stu-id="cf122-288">Member</span></span> | <span data-ttu-id="cf122-289">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="cf122-290">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-291">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="cf122-292">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-293">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-294">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="cf122-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="cf122-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="cf122-296">member</span><span class="sxs-lookup"><span data-stu-id="cf122-296">Member</span></span> | <span data-ttu-id="cf122-297">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cf122-298">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-299">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="cf122-300">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="cf122-301">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="cf122-302">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="cf122-303">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="cf122-304">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="cf122-305">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="cf122-306">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="cf122-307">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="cf122-308">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="cf122-309">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="cf122-310">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="cf122-311">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="cf122-312">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="cf122-313">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cf122-314">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-315">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-316">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-317">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="cf122-318">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cf122-319">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-320">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-321">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="cf122-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-322">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-323">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="cf122-324">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="cf122-325">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="cf122-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="cf122-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="cf122-327">member</span><span class="sxs-lookup"><span data-stu-id="cf122-327">Member</span></span> | <span data-ttu-id="cf122-328">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="cf122-329">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="cf122-330">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="cf122-331">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="cf122-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="cf122-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="cf122-333">member</span><span class="sxs-lookup"><span data-stu-id="cf122-333">Member</span></span> | <span data-ttu-id="cf122-334">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-335">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-336">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-337">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-337">All</span></span> |
| <span data-ttu-id="cf122-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="cf122-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="cf122-339">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="cf122-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="cf122-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="cf122-341">member</span><span class="sxs-lookup"><span data-stu-id="cf122-341">Member</span></span> | <span data-ttu-id="cf122-342">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-343">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="cf122-344">系統安全性原則</span><span class="sxs-lookup"><span data-stu-id="cf122-344">System.Security.Policy</span></span>

| <span data-ttu-id="cf122-345">member</span><span class="sxs-lookup"><span data-stu-id="cf122-345">Member</span></span> | <span data-ttu-id="cf122-346">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-347">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="cf122-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="cf122-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="cf122-349">member</span><span class="sxs-lookup"><span data-stu-id="cf122-349">Member</span></span> | <span data-ttu-id="cf122-350">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-351">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="cf122-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="cf122-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="cf122-353">member</span><span class="sxs-lookup"><span data-stu-id="cf122-353">Member</span></span> | <span data-ttu-id="cf122-354">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-355">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="cf122-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="cf122-356">System.Threading</span></span>

| <span data-ttu-id="cf122-357">member</span><span class="sxs-lookup"><span data-stu-id="cf122-357">Member</span></span> | <span data-ttu-id="cf122-358">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-359">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="cf122-360">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="cf122-361">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="cf122-362">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="cf122-363">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="cf122-364">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="cf122-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="cf122-365">System.Xml</span></span>

| <span data-ttu-id="cf122-366">member</span><span class="sxs-lookup"><span data-stu-id="cf122-366">Member</span></span> | <span data-ttu-id="cf122-367">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="cf122-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="cf122-368">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="cf122-369">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="cf122-370">全部</span><span class="sxs-lookup"><span data-stu-id="cf122-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="cf122-371">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf122-371">See also</span></span>

- [<span data-ttu-id="cf122-372">從 .NET Framework 遷移至 .NET Core 的突破性變更</span><span class="sxs-lookup"><span data-stu-id="cf122-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="cf122-373">.NET Core 中的二進位序列化</span><span class="sxs-lookup"><span data-stu-id="cf122-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="cf122-374">.NET 可攜性分析器</span><span class="sxs-lookup"><span data-stu-id="cf122-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
