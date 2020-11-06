---
title: .NET Core 和 .NET 5 + 上不支援的 Api
titleSuffix: ''
description: 瞭解哪些 .NET Api 一律會在 .NET Core 和 .NET 5.0 和更新版本上擲回例外狀況。
ms.date: 10/13/2020
ms.openlocfilehash: 51d73557a48910d9cb1c4d3cdced34dfe4d849d8
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329777"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="4d0b1-103">在 .NET Core 和 .NET 5 + 上一律會擲回例外狀況的 Api</span><span class="sxs-lookup"><span data-stu-id="4d0b1-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="4d0b1-104">下列 Api 一律會 <xref:System.PlatformNotSupportedException> 在 .net 5.0 和更新版本上擲回， (包括所有或平臺子集上的所有 .Net Core 版本) 。</span><span class="sxs-lookup"><span data-stu-id="4d0b1-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="4d0b1-105">本文會依命名空間來組織受影響的 Api。</span><span class="sxs-lookup"><span data-stu-id="4d0b1-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="4d0b1-106">本文是進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="4d0b1-106">This article is a work-in-progress.</span></span> <span data-ttu-id="4d0b1-107">它不是在 .NET 5 + 上擲回例外狀況的完整 Api 清單。</span><span class="sxs-lookup"><span data-stu-id="4d0b1-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="4d0b1-108">本文不包含在 .NET 5 + 上擲回之二進位序列化的明確介面執行。</span><span class="sxs-lookup"><span data-stu-id="4d0b1-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="4d0b1-109">如需詳細資訊，請參閱 [.Net Core 中的二進位序列化](../../standard/serialization/binary-serialization.md#net-core)。</span><span class="sxs-lookup"><span data-stu-id="4d0b1-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="4d0b1-110">系統</span><span class="sxs-lookup"><span data-stu-id="4d0b1-110">System</span></span>

| <span data-ttu-id="4d0b1-111">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-111">Member</span></span> | <span data-ttu-id="4d0b1-112">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-113">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-114">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-115">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-116">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-117">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-118">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-119">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-120">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-121">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-122">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="4d0b1-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="4d0b1-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="4d0b1-124">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-124">Member</span></span> | <span data-ttu-id="4d0b1-125">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-126">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-127">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-128">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="4d0b1-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="4d0b1-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="4d0b1-130">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-130">Member</span></span> | <span data-ttu-id="4d0b1-131">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-132">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-133">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-134">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="4d0b1-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="4d0b1-135">System.Configuration</span></span>

| <span data-ttu-id="4d0b1-136">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-136">Member</span></span> | <span data-ttu-id="4d0b1-137">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="4d0b1-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (所有成員) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="4d0b1-139">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="4d0b1-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="4d0b1-140">System.Console</span></span>

| <span data-ttu-id="4d0b1-141">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-141">Member</span></span> | <span data-ttu-id="4d0b1-142">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-143">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-143">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-145">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-145">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-147">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-147">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-149">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-149">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (只取得) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="4d0b1-151">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-152">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-153">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-154">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-154">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-155"><xref:System.Console.Title?displayProperty=nameWithType> (只取得) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="4d0b1-156">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-156">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-158">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-158">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-160">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-160">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-162">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-162">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-164">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="4d0b1-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="4d0b1-165">System.Data.Common</span></span>

| <span data-ttu-id="4d0b1-166">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-166">Member</span></span> | <span data-ttu-id="4d0b1-167">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="4d0b1-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (擲回 <xref:System.NotSupportedException>) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="4d0b1-169">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="4d0b1-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="4d0b1-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="4d0b1-171">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-171">Member</span></span> | <span data-ttu-id="4d0b1-172">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="4d0b1-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-174">Linux</span><span class="sxs-lookup"><span data-stu-id="4d0b1-174">Linux</span></span> |
| <span data-ttu-id="4d0b1-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-176">Linux</span><span class="sxs-lookup"><span data-stu-id="4d0b1-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-177">macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-178">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-179">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-180">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-181">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-182">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-183">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-183">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-185">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-185">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (只取得) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="4d0b1-187">macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-187">macOS</span></span> |
| <span data-ttu-id="4d0b1-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-189">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="4d0b1-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="4d0b1-190">System.IO</span></span>

| <span data-ttu-id="4d0b1-191">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-191">Member</span></span> | <span data-ttu-id="4d0b1-192">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-193">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-194">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="4d0b1-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="4d0b1-195">System.IO.Pipes</span></span>

| <span data-ttu-id="4d0b1-196">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-196">Member</span></span> | <span data-ttu-id="4d0b1-197">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-198">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-199">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-200">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-201">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-201">Linux and macOS</span></span> |
| <span data-ttu-id="4d0b1-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-203">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-204">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="4d0b1-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="4d0b1-205">System.Media</span></span>

| <span data-ttu-id="4d0b1-206">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-206">Member</span></span> | <span data-ttu-id="4d0b1-207">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-208">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="4d0b1-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="4d0b1-209">System.Net</span></span>

| <span data-ttu-id="4d0b1-210">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-210">Member</span></span> | <span data-ttu-id="4d0b1-211">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-212">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-213">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-214">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-215">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-216">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-217">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-218">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-219">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-220">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-221">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-222">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-223">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-224">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-225">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-226">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-227">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-228">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="4d0b1-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="4d0b1-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="4d0b1-230">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-230">Member</span></span> | <span data-ttu-id="4d0b1-231">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-232">Windows (UWP) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="4d0b1-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="4d0b1-233">System.Net.Sockets</span></span>

| <span data-ttu-id="4d0b1-234">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-234">Member</span></span> | <span data-ttu-id="4d0b1-235">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="4d0b1-236">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-237">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="4d0b1-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="4d0b1-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="4d0b1-239">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-239">Member</span></span> | <span data-ttu-id="4d0b1-240">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-241">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="4d0b1-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="4d0b1-242">System.Reflection</span></span>

| <span data-ttu-id="4d0b1-243">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-243">Member</span></span> | <span data-ttu-id="4d0b1-244">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-245">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-246">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-247">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-248">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="4d0b1-249">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-250">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-251">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="4d0b1-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="4d0b1-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="4d0b1-253">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-253">Member</span></span> | <span data-ttu-id="4d0b1-254">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-255">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="4d0b1-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="4d0b1-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="4d0b1-257">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-257">Member</span></span> | <span data-ttu-id="4d0b1-258">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-259">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-260">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-261">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-262">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-263">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-264">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-265">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="4d0b1-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="4d0b1-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="4d0b1-267">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-267">Member</span></span> | <span data-ttu-id="4d0b1-268">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-269">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="4d0b1-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="4d0b1-270">System.Security</span></span>

| <span data-ttu-id="4d0b1-271">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-271">Member</span></span> | <span data-ttu-id="4d0b1-272">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-273">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-274">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-275">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-276">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-277">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-278">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-279">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-280">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-281">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-282">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-283">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-284">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-285">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-286">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="4d0b1-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="4d0b1-287">System.Security.Claims</span></span>

| <span data-ttu-id="4d0b1-288">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-288">Member</span></span> | <span data-ttu-id="4d0b1-289">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-290">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-291">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="4d0b1-292">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-293">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-294">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="4d0b1-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="4d0b1-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="4d0b1-296">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-296">Member</span></span> | <span data-ttu-id="4d0b1-297">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-298">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="4d0b1-299">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-300">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-301">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-302">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-303">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-304">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-305">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-306">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-307">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-308">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-309">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-310">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-311">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-312">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-313">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-314">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-315">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-316">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-317">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-318">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-319">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-320">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-321">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4d0b1-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-322">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-323">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-324">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-325">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="4d0b1-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="4d0b1-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="4d0b1-327">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-327">Member</span></span> | <span data-ttu-id="4d0b1-328">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="4d0b1-329">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-330">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="4d0b1-331">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="4d0b1-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="4d0b1-332">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-332">Member</span></span> | <span data-ttu-id="4d0b1-333">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-334">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-335">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-336">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-336">All</span></span> |
| <span data-ttu-id="4d0b1-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> 僅 (設定) </span><span class="sxs-lookup"><span data-stu-id="4d0b1-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4d0b1-338">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="4d0b1-339">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="4d0b1-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="4d0b1-340">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-340">Member</span></span> | <span data-ttu-id="4d0b1-341">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-342">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="4d0b1-343">系統安全性原則</span><span class="sxs-lookup"><span data-stu-id="4d0b1-343">System.Security.Policy</span></span>

| <span data-ttu-id="4d0b1-344">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-344">Member</span></span> | <span data-ttu-id="4d0b1-345">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-346">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="4d0b1-347">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="4d0b1-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="4d0b1-348">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-348">Member</span></span> | <span data-ttu-id="4d0b1-349">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="4d0b1-350">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="4d0b1-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="4d0b1-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="4d0b1-352">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-352">Member</span></span> | <span data-ttu-id="4d0b1-353">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-354">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="4d0b1-355">System.Threading</span><span class="sxs-lookup"><span data-stu-id="4d0b1-355">System.Threading</span></span>

| <span data-ttu-id="4d0b1-356">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-356">Member</span></span> | <span data-ttu-id="4d0b1-357">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-358">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-359">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-360">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-361">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-362">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-363">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="4d0b1-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="4d0b1-364">System.Xml</span></span>

| <span data-ttu-id="4d0b1-365">成員</span><span class="sxs-lookup"><span data-stu-id="4d0b1-365">Member</span></span> | <span data-ttu-id="4d0b1-366">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4d0b1-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-367">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-368">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="4d0b1-369">全部</span><span class="sxs-lookup"><span data-stu-id="4d0b1-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="4d0b1-370">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d0b1-370">See also</span></span>

- [<span data-ttu-id="4d0b1-371">從 .NET Framework 遷移至 .NET Core 的重大變更</span><span class="sxs-lookup"><span data-stu-id="4d0b1-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="4d0b1-372">.NET Core 中的二進位序列化</span><span class="sxs-lookup"><span data-stu-id="4d0b1-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="4d0b1-373">.NET 可攜性分析器</span><span class="sxs-lookup"><span data-stu-id="4d0b1-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
