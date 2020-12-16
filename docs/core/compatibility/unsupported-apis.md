---
title: .NET Core 和 .NET 5 + 上不支援的 Api
titleSuffix: ''
description: 瞭解哪些 .NET Api 一律會在 .NET Core 和 .NET 5.0 和更新版本上擲回例外狀況。
ms.date: 10/13/2020
ms.openlocfilehash: 1bd41192d0d6752d2b659da9fb6387dac321b2c3
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593262"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="62b27-103">在 .NET Core 和 .NET 5 + 上一律會擲回例外狀況的 Api</span><span class="sxs-lookup"><span data-stu-id="62b27-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="62b27-104">下列 Api 一律會 <xref:System.PlatformNotSupportedException> 在 .net 5.0 和更新版本上擲回， (包括所有或平臺子集上的所有 .Net Core 版本) 。</span><span class="sxs-lookup"><span data-stu-id="62b27-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="62b27-105">本文會依命名空間來組織受影響的 Api。</span><span class="sxs-lookup"><span data-stu-id="62b27-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="62b27-106">本文是進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="62b27-106">This article is a work-in-progress.</span></span> <span data-ttu-id="62b27-107">它不是在 .NET 5 + 上擲回例外狀況的完整 Api 清單。</span><span class="sxs-lookup"><span data-stu-id="62b27-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="62b27-108">本文不包含在 .NET 5 + 上擲回之二進位序列化的明確介面執行。</span><span class="sxs-lookup"><span data-stu-id="62b27-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="62b27-109">如需詳細資訊，請參閱 [.Net Core 中的二進位序列化](../../standard/serialization/binary-serialization.md#net-core)。</span><span class="sxs-lookup"><span data-stu-id="62b27-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="62b27-110">System</span><span class="sxs-lookup"><span data-stu-id="62b27-110">System</span></span>

| <span data-ttu-id="62b27-111">member</span><span class="sxs-lookup"><span data-stu-id="62b27-111">Member</span></span> | <span data-ttu-id="62b27-112">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-113">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="62b27-114">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="62b27-115">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="62b27-116">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-117">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="62b27-118">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="62b27-119">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="62b27-120">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-121">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="62b27-122">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="62b27-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="62b27-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="62b27-124">member</span><span class="sxs-lookup"><span data-stu-id="62b27-124">Member</span></span> | <span data-ttu-id="62b27-125">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-126">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-127">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-128">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="62b27-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="62b27-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="62b27-130">member</span><span class="sxs-lookup"><span data-stu-id="62b27-130">Member</span></span> | <span data-ttu-id="62b27-131">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-132">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-133">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="62b27-134">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="62b27-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="62b27-135">System.Configuration</span></span>

| <span data-ttu-id="62b27-136">member</span><span class="sxs-lookup"><span data-stu-id="62b27-136">Member</span></span> | <span data-ttu-id="62b27-137">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="62b27-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (所有成員) </span><span class="sxs-lookup"><span data-stu-id="62b27-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="62b27-139">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="62b27-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="62b27-140">System.Console</span></span>

| <span data-ttu-id="62b27-141">member</span><span class="sxs-lookup"><span data-stu-id="62b27-141">Member</span></span> | <span data-ttu-id="62b27-142">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="62b27-143">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-143">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-145">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-145">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-147">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-147">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-149">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-149">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (只取得) </span><span class="sxs-lookup"><span data-stu-id="62b27-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="62b27-151">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-152">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-153">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-154">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-154">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-155"><xref:System.Console.Title?displayProperty=nameWithType> (只取得) </span><span class="sxs-lookup"><span data-stu-id="62b27-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="62b27-156">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-156">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-158">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-158">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-160">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-160">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-162">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-162">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-164">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="62b27-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="62b27-165">System.Data.Common</span></span>

| <span data-ttu-id="62b27-166">member</span><span class="sxs-lookup"><span data-stu-id="62b27-166">Member</span></span> | <span data-ttu-id="62b27-167">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="62b27-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (擲回 <xref:System.NotSupportedException>) </span><span class="sxs-lookup"><span data-stu-id="62b27-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="62b27-169">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="62b27-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="62b27-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="62b27-171">member</span><span class="sxs-lookup"><span data-stu-id="62b27-171">Member</span></span> | <span data-ttu-id="62b27-172">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="62b27-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-174">Linux</span><span class="sxs-lookup"><span data-stu-id="62b27-174">Linux</span></span> |
| <span data-ttu-id="62b27-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-176">Linux</span><span class="sxs-lookup"><span data-stu-id="62b27-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="62b27-177">macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="62b27-178">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="62b27-179">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="62b27-180">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="62b27-181">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="62b27-182">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="62b27-183">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-183">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="62b27-184">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-184">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-186">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-186">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (只取得) </span><span class="sxs-lookup"><span data-stu-id="62b27-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="62b27-188">macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-188">macOS</span></span> |
| <span data-ttu-id="62b27-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-190">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-190">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="62b27-191">System.IO</span><span class="sxs-lookup"><span data-stu-id="62b27-191">System.IO</span></span>

| <span data-ttu-id="62b27-192">member</span><span class="sxs-lookup"><span data-stu-id="62b27-192">Member</span></span> | <span data-ttu-id="62b27-193">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-193">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-194">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-194">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-195">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-195">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="62b27-196">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="62b27-196">System.IO.Pipes</span></span>

| <span data-ttu-id="62b27-197">member</span><span class="sxs-lookup"><span data-stu-id="62b27-197">Member</span></span> | <span data-ttu-id="62b27-198">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-198">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="62b27-199">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="62b27-200">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="62b27-201">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-201">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="62b27-202">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-202">Linux and macOS</span></span> |
| <span data-ttu-id="62b27-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-204">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-204">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="62b27-205">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-205">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="62b27-206">System. Media</span><span class="sxs-lookup"><span data-stu-id="62b27-206">System.Media</span></span>

| <span data-ttu-id="62b27-207">member</span><span class="sxs-lookup"><span data-stu-id="62b27-207">Member</span></span> | <span data-ttu-id="62b27-208">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-208">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-209">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-209">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="62b27-210">System.Net</span><span class="sxs-lookup"><span data-stu-id="62b27-210">System.Net</span></span>

| <span data-ttu-id="62b27-211">member</span><span class="sxs-lookup"><span data-stu-id="62b27-211">Member</span></span> | <span data-ttu-id="62b27-212">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-212">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="62b27-213">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-213">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="62b27-214">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-214">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-215">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-215">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-216">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-216">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-217">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-217">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-218">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-219">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-219">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-220">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-221">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-221">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-222">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-222">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-223">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-223">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="62b27-224">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-224">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-225">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-225">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-226">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-226">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-227">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-227">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-228">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-228">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-229">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-229">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="62b27-230">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="62b27-230">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="62b27-231">member</span><span class="sxs-lookup"><span data-stu-id="62b27-231">Member</span></span> | <span data-ttu-id="62b27-232">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-232">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-233">Windows (UWP) </span><span class="sxs-lookup"><span data-stu-id="62b27-233">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="62b27-234">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="62b27-234">System.Net.Sockets</span></span>

| <span data-ttu-id="62b27-235">member</span><span class="sxs-lookup"><span data-stu-id="62b27-235">Member</span></span> | <span data-ttu-id="62b27-236">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-236">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="62b27-237">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-237">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="62b27-238">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-238">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="62b27-239">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="62b27-239">System.Net.WebSockets</span></span>

| <span data-ttu-id="62b27-240">member</span><span class="sxs-lookup"><span data-stu-id="62b27-240">Member</span></span> | <span data-ttu-id="62b27-241">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-241">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="62b27-242">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-242">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="62b27-243">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="62b27-243">System.Reflection</span></span>

| <span data-ttu-id="62b27-244">member</span><span class="sxs-lookup"><span data-stu-id="62b27-244">Member</span></span> | <span data-ttu-id="62b27-245">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-245">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-246">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-246">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="62b27-247">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-248">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-248">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="62b27-249">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="62b27-250">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-251">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-251">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="62b27-252">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-252">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="62b27-253">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="62b27-253">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="62b27-254">member</span><span class="sxs-lookup"><span data-stu-id="62b27-254">Member</span></span> | <span data-ttu-id="62b27-255">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-255">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="62b27-256">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-256">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="62b27-257">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="62b27-257">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="62b27-258">member</span><span class="sxs-lookup"><span data-stu-id="62b27-258">Member</span></span> | <span data-ttu-id="62b27-259">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-259">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="62b27-260">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="62b27-261">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="62b27-262">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-262">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="62b27-263">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-263">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="62b27-264">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="62b27-265">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-265">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="62b27-266">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-266">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="62b27-267">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="62b27-267">System.Runtime.Serialization</span></span>

| <span data-ttu-id="62b27-268">member</span><span class="sxs-lookup"><span data-stu-id="62b27-268">Member</span></span> | <span data-ttu-id="62b27-269">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-269">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="62b27-270">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-270">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="62b27-271">System.Security</span><span class="sxs-lookup"><span data-stu-id="62b27-271">System.Security</span></span>

| <span data-ttu-id="62b27-272">member</span><span class="sxs-lookup"><span data-stu-id="62b27-272">Member</span></span> | <span data-ttu-id="62b27-273">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-273">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="62b27-274">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-274">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="62b27-275">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-275">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="62b27-276">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-276">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="62b27-277">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-277">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="62b27-278">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-278">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="62b27-279">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-279">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="62b27-280">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-280">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="62b27-281">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="62b27-282">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-282">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="62b27-283">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-283">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="62b27-284">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-284">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="62b27-285">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="62b27-286">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-286">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="62b27-287">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-287">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="62b27-288">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="62b27-288">System.Security.Claims</span></span>

| <span data-ttu-id="62b27-289">member</span><span class="sxs-lookup"><span data-stu-id="62b27-289">Member</span></span> | <span data-ttu-id="62b27-290">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-290">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-291">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-292">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="62b27-293">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-294">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-294">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-295">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-295">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="62b27-296">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="62b27-296">System.Security.Cryptography</span></span>

| <span data-ttu-id="62b27-297">member</span><span class="sxs-lookup"><span data-stu-id="62b27-297">Member</span></span> | <span data-ttu-id="62b27-298">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-298">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="62b27-299">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-299">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="62b27-300">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="62b27-301">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="62b27-302">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="62b27-303">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="62b27-304">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="62b27-305">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="62b27-306">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="62b27-307">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="62b27-308">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="62b27-309">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="62b27-310">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="62b27-311">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="62b27-312">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-312">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="62b27-313">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="62b27-314">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="62b27-315">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-316">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-317">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-317">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-318">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="62b27-319">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-319">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="62b27-320">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-320">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-321">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-322">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="62b27-322">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-323">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-323">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-324">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="62b27-325">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-325">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="62b27-326">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-326">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="62b27-327">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="62b27-327">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="62b27-328">member</span><span class="sxs-lookup"><span data-stu-id="62b27-328">Member</span></span> | <span data-ttu-id="62b27-329">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-329">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="62b27-330">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="62b27-331">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="62b27-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="62b27-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="62b27-333">member</span><span class="sxs-lookup"><span data-stu-id="62b27-333">Member</span></span> | <span data-ttu-id="62b27-334">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-335">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-336">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-337">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-337">All</span></span> |
| <span data-ttu-id="62b27-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="62b27-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="62b27-339">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="62b27-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="62b27-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="62b27-341">member</span><span class="sxs-lookup"><span data-stu-id="62b27-341">Member</span></span> | <span data-ttu-id="62b27-342">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-343">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="62b27-344">系統安全性原則</span><span class="sxs-lookup"><span data-stu-id="62b27-344">System.Security.Policy</span></span>

| <span data-ttu-id="62b27-345">member</span><span class="sxs-lookup"><span data-stu-id="62b27-345">Member</span></span> | <span data-ttu-id="62b27-346">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-347">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="62b27-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="62b27-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="62b27-349">member</span><span class="sxs-lookup"><span data-stu-id="62b27-349">Member</span></span> | <span data-ttu-id="62b27-350">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="62b27-351">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="62b27-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="62b27-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="62b27-353">member</span><span class="sxs-lookup"><span data-stu-id="62b27-353">Member</span></span> | <span data-ttu-id="62b27-354">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-355">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="62b27-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="62b27-356">System.Threading</span></span>

| <span data-ttu-id="62b27-357">member</span><span class="sxs-lookup"><span data-stu-id="62b27-357">Member</span></span> | <span data-ttu-id="62b27-358">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-359">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="62b27-360">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="62b27-361">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="62b27-362">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="62b27-363">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="62b27-364">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="62b27-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="62b27-365">System.Xml</span></span>

| <span data-ttu-id="62b27-366">member</span><span class="sxs-lookup"><span data-stu-id="62b27-366">Member</span></span> | <span data-ttu-id="62b27-367">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="62b27-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="62b27-368">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="62b27-369">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="62b27-370">全部</span><span class="sxs-lookup"><span data-stu-id="62b27-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="62b27-371">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62b27-371">See also</span></span>

- [<span data-ttu-id="62b27-372">從 .NET Framework 遷移至 .NET Core 的重大變更</span><span class="sxs-lookup"><span data-stu-id="62b27-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="62b27-373">.NET Core 中的二進位序列化</span><span class="sxs-lookup"><span data-stu-id="62b27-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="62b27-374">.NET 可攜性分析器</span><span class="sxs-lookup"><span data-stu-id="62b27-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
