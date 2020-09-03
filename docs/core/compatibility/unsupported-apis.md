---
title: .NET Core 上不支援的 Api
titleSuffix: ''
description: 瞭解 .NET Framework 中一律會在 .NET Core 上擲回例外狀況的 Api。
ms.date: 12/23/2019
ms.openlocfilehash: 94f334d7e4b7daf407f489ba274172ced9eefa81
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414431"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="434c4-103">一律會在 .NET Core 上擲回例外狀況的 Api</span><span class="sxs-lookup"><span data-stu-id="434c4-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="434c4-104">下列 Api 一律會在 <xref:System.PlatformNotSupportedException> 所有或部分平臺上的 .Net Core 上擲回。</span><span class="sxs-lookup"><span data-stu-id="434c4-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="434c4-105">本文會依命名空間來組織受影響的 API 成員。</span><span class="sxs-lookup"><span data-stu-id="434c4-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="434c4-106">本文是進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="434c4-106">This article is a work-in-progress.</span></span> <span data-ttu-id="434c4-107">它不是在 .NET Core 上擲回例外狀況的完整 Api 清單。</span><span class="sxs-lookup"><span data-stu-id="434c4-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="434c4-108">本文不包含在 .NET Core 上擲回之二進位序列化的明確介面執行。</span><span class="sxs-lookup"><span data-stu-id="434c4-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="434c4-109">如需詳細資訊，請參閱 [.Net Core 中的二進位序列化](../../standard/serialization/binary-serialization.md#net-core)。</span><span class="sxs-lookup"><span data-stu-id="434c4-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="434c4-110">系統</span><span class="sxs-lookup"><span data-stu-id="434c4-110">System</span></span>

| <span data-ttu-id="434c4-111">member</span><span class="sxs-lookup"><span data-stu-id="434c4-111">Member</span></span> | <span data-ttu-id="434c4-112">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-113">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="434c4-114">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="434c4-115">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="434c4-116">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-117">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="434c4-118">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="434c4-119">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="434c4-120">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-121">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="434c4-122">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="434c4-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="434c4-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="434c4-124">member</span><span class="sxs-lookup"><span data-stu-id="434c4-124">Member</span></span> | <span data-ttu-id="434c4-125">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-126">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-127">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-128">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="434c4-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="434c4-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="434c4-130">member</span><span class="sxs-lookup"><span data-stu-id="434c4-130">Member</span></span> | <span data-ttu-id="434c4-131">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-132">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-133">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="434c4-134">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="434c4-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="434c4-135">System.Configuration</span></span>

| <span data-ttu-id="434c4-136">member</span><span class="sxs-lookup"><span data-stu-id="434c4-136">Member</span></span> | <span data-ttu-id="434c4-137">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="434c4-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (所有成員) </span><span class="sxs-lookup"><span data-stu-id="434c4-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="434c4-139">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="434c4-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="434c4-140">System.Console</span></span>

| <span data-ttu-id="434c4-141">member</span><span class="sxs-lookup"><span data-stu-id="434c4-141">Member</span></span> | <span data-ttu-id="434c4-142">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="434c4-143">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-143">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-145">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-145">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-147">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-147">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-149">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-149">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (只取得) </span><span class="sxs-lookup"><span data-stu-id="434c4-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="434c4-151">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-152">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-153">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-154">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-154">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-155"><xref:System.Console.Title?displayProperty=nameWithType> (只取得) </span><span class="sxs-lookup"><span data-stu-id="434c4-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="434c4-156">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-156">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-158">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-158">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-160">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-160">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-162">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-162">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-164">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="434c4-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="434c4-165">System.Data.Common</span></span>

| <span data-ttu-id="434c4-166">member</span><span class="sxs-lookup"><span data-stu-id="434c4-166">Member</span></span> | <span data-ttu-id="434c4-167">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="434c4-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (擲回 <xref:System.NotSupportedException>) </span><span class="sxs-lookup"><span data-stu-id="434c4-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="434c4-169">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="434c4-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="434c4-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="434c4-171">member</span><span class="sxs-lookup"><span data-stu-id="434c4-171">Member</span></span> | <span data-ttu-id="434c4-172">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="434c4-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-174">Linux</span><span class="sxs-lookup"><span data-stu-id="434c4-174">Linux</span></span> |
| <span data-ttu-id="434c4-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-176">Linux</span><span class="sxs-lookup"><span data-stu-id="434c4-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="434c4-177">macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="434c4-178">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-179">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="434c4-180">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="434c4-181">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="434c4-182">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="434c4-183">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-183">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-185">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-185">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (只取得) </span><span class="sxs-lookup"><span data-stu-id="434c4-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="434c4-187">macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-187">macOS</span></span> |
| <span data-ttu-id="434c4-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-189">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="434c4-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="434c4-190">System.IO</span></span>

| <span data-ttu-id="434c4-191">member</span><span class="sxs-lookup"><span data-stu-id="434c4-191">Member</span></span> | <span data-ttu-id="434c4-192">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-193">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-194">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="434c4-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="434c4-195">System.IO.Pipes</span></span>

| <span data-ttu-id="434c4-196">member</span><span class="sxs-lookup"><span data-stu-id="434c4-196">Member</span></span> | <span data-ttu-id="434c4-197">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="434c4-198">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="434c4-199">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="434c4-200">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="434c4-201">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-201">Linux and macOS</span></span> |
| <span data-ttu-id="434c4-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-203">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="434c4-204">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="434c4-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="434c4-205">System.Media</span></span>

| <span data-ttu-id="434c4-206">member</span><span class="sxs-lookup"><span data-stu-id="434c4-206">Member</span></span> | <span data-ttu-id="434c4-207">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-208">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="434c4-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="434c4-209">System.Net</span></span>

| <span data-ttu-id="434c4-210">member</span><span class="sxs-lookup"><span data-stu-id="434c4-210">Member</span></span> | <span data-ttu-id="434c4-211">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="434c4-212">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="434c4-213">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-214">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-215">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-216">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-217">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-218">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-219">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-220">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-221">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-222">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="434c4-223">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-224">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-225">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-226">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-227">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-228">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="434c4-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="434c4-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="434c4-230">member</span><span class="sxs-lookup"><span data-stu-id="434c4-230">Member</span></span> | <span data-ttu-id="434c4-231">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-232">Windows (UWP) </span><span class="sxs-lookup"><span data-stu-id="434c4-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="434c4-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="434c4-233">System.Net.Sockets</span></span>

| <span data-ttu-id="434c4-234">member</span><span class="sxs-lookup"><span data-stu-id="434c4-234">Member</span></span> | <span data-ttu-id="434c4-235">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="434c4-236">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="434c4-237">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="434c4-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="434c4-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="434c4-239">member</span><span class="sxs-lookup"><span data-stu-id="434c4-239">Member</span></span> | <span data-ttu-id="434c4-240">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="434c4-241">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="434c4-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="434c4-242">System.Reflection</span></span>

| <span data-ttu-id="434c4-243">member</span><span class="sxs-lookup"><span data-stu-id="434c4-243">Member</span></span> | <span data-ttu-id="434c4-244">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-245">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="434c4-246">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-247">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="434c4-248">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="434c4-249">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-250">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="434c4-251">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="434c4-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="434c4-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="434c4-253">member</span><span class="sxs-lookup"><span data-stu-id="434c4-253">Member</span></span> | <span data-ttu-id="434c4-254">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="434c4-255">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="434c4-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="434c4-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="434c4-257">member</span><span class="sxs-lookup"><span data-stu-id="434c4-257">Member</span></span> | <span data-ttu-id="434c4-258">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="434c4-259">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="434c4-260">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="434c4-261">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="434c4-262">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="434c4-263">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="434c4-264">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="434c4-265">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="434c4-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="434c4-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="434c4-267">member</span><span class="sxs-lookup"><span data-stu-id="434c4-267">Member</span></span> | <span data-ttu-id="434c4-268">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="434c4-269">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="434c4-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="434c4-270">System.Security</span></span>

| <span data-ttu-id="434c4-271">member</span><span class="sxs-lookup"><span data-stu-id="434c4-271">Member</span></span> | <span data-ttu-id="434c4-272">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="434c4-273">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="434c4-274">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="434c4-275">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="434c4-276">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="434c4-277">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="434c4-278">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="434c4-279">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="434c4-280">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="434c4-281">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="434c4-282">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="434c4-283">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="434c4-284">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="434c4-285">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="434c4-286">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="434c4-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="434c4-287">System.Security.Claims</span></span>

| <span data-ttu-id="434c4-288">member</span><span class="sxs-lookup"><span data-stu-id="434c4-288">Member</span></span> | <span data-ttu-id="434c4-289">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="434c4-290">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-291">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="434c4-292">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-293">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-294">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="434c4-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="434c4-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="434c4-296">member</span><span class="sxs-lookup"><span data-stu-id="434c4-296">Member</span></span> | <span data-ttu-id="434c4-297">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="434c4-298">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="434c4-299">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="434c4-300">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="434c4-301">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="434c4-302">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="434c4-303">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="434c4-304">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="434c4-305">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="434c4-306">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="434c4-307">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="434c4-308">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="434c4-309">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="434c4-310">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="434c4-311">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="434c4-312">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="434c4-313">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="434c4-314">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-315">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-316">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-317">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="434c4-318">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="434c4-319">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-320">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-321">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="434c4-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-322">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-323">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="434c4-324">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="434c4-325">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="434c4-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="434c4-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="434c4-327">member</span><span class="sxs-lookup"><span data-stu-id="434c4-327">Member</span></span> | <span data-ttu-id="434c4-328">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="434c4-329">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="434c4-330">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="434c4-331">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="434c4-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="434c4-332">member</span><span class="sxs-lookup"><span data-stu-id="434c4-332">Member</span></span> | <span data-ttu-id="434c4-333">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-334">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-335">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-336">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-336">All</span></span> |
| <span data-ttu-id="434c4-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="434c4-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="434c4-338">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="434c4-339">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="434c4-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="434c4-340">member</span><span class="sxs-lookup"><span data-stu-id="434c4-340">Member</span></span> | <span data-ttu-id="434c4-341">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-342">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="434c4-343">系統安全性原則</span><span class="sxs-lookup"><span data-stu-id="434c4-343">System.Security.Policy</span></span>

| <span data-ttu-id="434c4-344">member</span><span class="sxs-lookup"><span data-stu-id="434c4-344">Member</span></span> | <span data-ttu-id="434c4-345">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-346">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="434c4-347">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="434c4-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="434c4-348">member</span><span class="sxs-lookup"><span data-stu-id="434c4-348">Member</span></span> | <span data-ttu-id="434c4-349">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="434c4-350">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="434c4-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="434c4-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="434c4-352">member</span><span class="sxs-lookup"><span data-stu-id="434c4-352">Member</span></span> | <span data-ttu-id="434c4-353">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-354">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="434c4-355">System.Threading</span><span class="sxs-lookup"><span data-stu-id="434c4-355">System.Threading</span></span>

| <span data-ttu-id="434c4-356">member</span><span class="sxs-lookup"><span data-stu-id="434c4-356">Member</span></span> | <span data-ttu-id="434c4-357">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-358">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="434c4-359">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="434c4-360">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="434c4-361">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="434c4-362">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="434c4-363">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="434c4-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="434c4-364">System.Xml</span></span>

| <span data-ttu-id="434c4-365">member</span><span class="sxs-lookup"><span data-stu-id="434c4-365">Member</span></span> | <span data-ttu-id="434c4-366">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="434c4-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="434c4-367">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="434c4-368">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="434c4-369">全部</span><span class="sxs-lookup"><span data-stu-id="434c4-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="434c4-370">另請參閱</span><span class="sxs-lookup"><span data-stu-id="434c4-370">See also</span></span>

- [<span data-ttu-id="434c4-371">從 .NET Framework 遷移至 .NET Core 的重大變更</span><span class="sxs-lookup"><span data-stu-id="434c4-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="434c4-372">.NET Core 中的二進位序列化</span><span class="sxs-lookup"><span data-stu-id="434c4-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="434c4-373">.NET 可攜性分析器</span><span class="sxs-lookup"><span data-stu-id="434c4-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
