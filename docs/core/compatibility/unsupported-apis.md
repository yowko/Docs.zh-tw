---
title: .NET Core 上不支援的 Api
description: 瞭解 .NET Framework 中一律會在 .NET Core 上擲回例外狀況的 Api。
ms.date: 12/23/2019
ms.openlocfilehash: f27aeca31226a95dacf100813762eedb56876fbd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936979"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="4eb10-103">在 .NET Core 上一律會擲回例外狀況的 Api</span><span class="sxs-lookup"><span data-stu-id="4eb10-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="4eb10-104">下列 Api 一律會在所有或部分平臺的 .NET Core 上擲回 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="4eb10-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="4eb10-105">本文會依照命名空間來組織受影響的 API 成員。</span><span class="sxs-lookup"><span data-stu-id="4eb10-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="4eb10-106">這篇文章是一個進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="4eb10-106">This article is a work-in-progress.</span></span> <span data-ttu-id="4eb10-107">這不是在 .NET Core 上擲回例外狀況的完整 Api 清單。</span><span class="sxs-lookup"><span data-stu-id="4eb10-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="4eb10-108">本文不包含在 .NET Core 上擲回之二進位序列化的明確介面執行。</span><span class="sxs-lookup"><span data-stu-id="4eb10-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="4eb10-109">如需詳細資訊，請參閱[.Net Core 中的二進位序列化](../../standard/serialization/binary-serialization.md#net-core)。</span><span class="sxs-lookup"><span data-stu-id="4eb10-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="4eb10-110">System</span><span class="sxs-lookup"><span data-stu-id="4eb10-110">System</span></span>

| <span data-ttu-id="4eb10-111">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-111">Member</span></span> | <span data-ttu-id="4eb10-112">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-113">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-114">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="4eb10-115">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="4eb10-116">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-117">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="4eb10-118">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="4eb10-119">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="4eb10-120">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-121">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-122">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="4eb10-123">{2&gt;System.CodeDom.Compiler&lt;2}</span><span class="sxs-lookup"><span data-stu-id="4eb10-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="4eb10-124">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-124">Member</span></span> | <span data-ttu-id="4eb10-125">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-126">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-127">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-128">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="4eb10-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="4eb10-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="4eb10-130">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-130">Member</span></span> | <span data-ttu-id="4eb10-131">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-132">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-133">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-134">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="4eb10-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="4eb10-135">System.Configuration</span></span>

| <span data-ttu-id="4eb10-136">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-136">Member</span></span> | <span data-ttu-id="4eb10-137">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="4eb10-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> （所有成員）</span><span class="sxs-lookup"><span data-stu-id="4eb10-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="4eb10-139">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="4eb10-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="4eb10-140">System.Console</span></span>

| <span data-ttu-id="4eb10-141">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-141">Member</span></span> | <span data-ttu-id="4eb10-142">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="4eb10-143">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-143">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-145">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-145">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-147">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-147">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-149">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-149">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> （僅限取得）</span><span class="sxs-lookup"><span data-stu-id="4eb10-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="4eb10-151">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-152">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-153">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-154">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-154">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-155"><xref:System.Console.Title?displayProperty=nameWithType> （僅限取得）</span><span class="sxs-lookup"><span data-stu-id="4eb10-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="4eb10-156">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-156">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-158">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-158">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-160">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-160">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-162">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-162">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-164">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="4eb10-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="4eb10-165">System.Data.Common</span></span>

| <span data-ttu-id="4eb10-166">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-166">Member</span></span> | <span data-ttu-id="4eb10-167">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="4eb10-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> （擲回 <xref:System.NotSupportedException>）</span><span class="sxs-lookup"><span data-stu-id="4eb10-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="4eb10-169">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="4eb10-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="4eb10-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="4eb10-171">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-171">Member</span></span> | <span data-ttu-id="4eb10-172">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="4eb10-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-174">Linux</span><span class="sxs-lookup"><span data-stu-id="4eb10-174">Linux</span></span> |
| <span data-ttu-id="4eb10-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-176">Linux</span><span class="sxs-lookup"><span data-stu-id="4eb10-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="4eb10-177">macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="4eb10-178">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-179">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="4eb10-180">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="4eb10-181">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="4eb10-182">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="4eb10-183">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-183">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-185">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-185">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> （僅限取得）</span><span class="sxs-lookup"><span data-stu-id="4eb10-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="4eb10-187">macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-187">macOS</span></span> |
| <span data-ttu-id="4eb10-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-189">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="4eb10-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="4eb10-190">System.IO</span></span>

| <span data-ttu-id="4eb10-191">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-191">Member</span></span> | <span data-ttu-id="4eb10-192">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-193">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-194">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="4eb10-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="4eb10-195">System.IO.Pipes</span></span>

| <span data-ttu-id="4eb10-196">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-196">Member</span></span> | <span data-ttu-id="4eb10-197">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="4eb10-198">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="4eb10-199">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="4eb10-200">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="4eb10-201">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-201">Linux and macOS</span></span> |
| <span data-ttu-id="4eb10-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-203">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="4eb10-204">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="4eb10-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="4eb10-205">System.Media</span></span>

| <span data-ttu-id="4eb10-206">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-206">Member</span></span> | <span data-ttu-id="4eb10-207">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-208">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="4eb10-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="4eb10-209">System.Net</span></span>

| <span data-ttu-id="4eb10-210">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-210">Member</span></span> | <span data-ttu-id="4eb10-211">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-212">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-213">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-214">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-215">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-216">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-217">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-218">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-219">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-220">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-221">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-222">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="4eb10-223">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-224">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-225">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-226">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-227">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-228">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="4eb10-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="4eb10-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="4eb10-230">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-230">Member</span></span> | <span data-ttu-id="4eb10-231">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="4eb10-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="4eb10-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="4eb10-233">System.Net.Sockets</span></span>

| <span data-ttu-id="4eb10-234">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-234">Member</span></span> | <span data-ttu-id="4eb10-235">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-236">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-236">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="4eb10-237">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="4eb10-237">System.Net.WebSockets</span></span>

| <span data-ttu-id="4eb10-238">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-238">Member</span></span> | <span data-ttu-id="4eb10-239">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-239">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="4eb10-240">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-240">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="4eb10-241">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="4eb10-241">System.Reflection</span></span>

| <span data-ttu-id="4eb10-242">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-242">Member</span></span> | <span data-ttu-id="4eb10-243">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-243">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-244">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-244">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-245">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-245">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-246">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-247">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-247">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-248">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-249">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="4eb10-250">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-250">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="4eb10-251">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="4eb10-251">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="4eb10-252">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-252">Member</span></span> | <span data-ttu-id="4eb10-253">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-253">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="4eb10-254">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-254">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="4eb10-255">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="4eb10-255">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="4eb10-256">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-256">Member</span></span> | <span data-ttu-id="4eb10-257">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-257">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-258">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-258">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="4eb10-259">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-260">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-261">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-261">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-262">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-262">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-263">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-264">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-264">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="4eb10-265">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="4eb10-265">System.Runtime.Serialization</span></span>

| <span data-ttu-id="4eb10-266">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-266">Member</span></span> | <span data-ttu-id="4eb10-267">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-267">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="4eb10-268">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-268">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="4eb10-269">System.Security</span><span class="sxs-lookup"><span data-stu-id="4eb10-269">System.Security</span></span>

| <span data-ttu-id="4eb10-270">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-270">Member</span></span> | <span data-ttu-id="4eb10-271">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-271">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="4eb10-272">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-272">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="4eb10-273">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-273">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-274">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-274">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="4eb10-275">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-275">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="4eb10-276">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-276">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="4eb10-277">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-277">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="4eb10-278">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-278">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="4eb10-279">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-279">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="4eb10-280">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="4eb10-281">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-281">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="4eb10-282">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-282">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-283">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-283">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="4eb10-284">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="4eb10-285">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-285">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="4eb10-286">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="4eb10-286">System.Security.Claims</span></span>

| <span data-ttu-id="4eb10-287">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-287">Member</span></span> | <span data-ttu-id="4eb10-288">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-288">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="4eb10-289">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-289">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-290">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-291">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-292">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-293">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-293">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="4eb10-294">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="4eb10-294">System.Security.Cryptography</span></span>

| <span data-ttu-id="4eb10-295">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-295">Member</span></span> | <span data-ttu-id="4eb10-296">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-296">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-297">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-297">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-298">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-298">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="4eb10-299">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="4eb10-300">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="4eb10-301">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="4eb10-302">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="4eb10-303">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="4eb10-304">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="4eb10-305">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="4eb10-306">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="4eb10-307">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="4eb10-308">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="4eb10-309">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="4eb10-310">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="4eb10-311">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-311">All</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-312">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="4eb10-313">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-314">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-315">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-316">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-317">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="4eb10-318">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-319">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-320">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-321">Linux 與 macOS</span><span class="sxs-lookup"><span data-stu-id="4eb10-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-322">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-323">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="4eb10-324">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-325">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="4eb10-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="4eb10-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="4eb10-327">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-327">Member</span></span> | <span data-ttu-id="4eb10-328">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-329">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-330">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="4eb10-331">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="4eb10-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="4eb10-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="4eb10-333">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-333">Member</span></span> | <span data-ttu-id="4eb10-334">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-335">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-336">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-337">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-337">All</span></span> |
| <span data-ttu-id="4eb10-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> （僅限設定）</span><span class="sxs-lookup"><span data-stu-id="4eb10-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="4eb10-339">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="4eb10-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="4eb10-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="4eb10-341">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-341">Member</span></span> | <span data-ttu-id="4eb10-342">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-343">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="4eb10-344">系統安全性原則</span><span class="sxs-lookup"><span data-stu-id="4eb10-344">System.Security.Policy</span></span>

| <span data-ttu-id="4eb10-345">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-345">Member</span></span> | <span data-ttu-id="4eb10-346">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-347">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="4eb10-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="4eb10-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="4eb10-349">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-349">Member</span></span> | <span data-ttu-id="4eb10-350">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-351">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="4eb10-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="4eb10-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="4eb10-353">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-353">Member</span></span> | <span data-ttu-id="4eb10-354">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-355">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="4eb10-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="4eb10-356">System.Threading</span></span>

| <span data-ttu-id="4eb10-357">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-357">Member</span></span> | <span data-ttu-id="4eb10-358">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-359">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-360">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="4eb10-361">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="4eb10-362">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="4eb10-363">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="4eb10-364">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="4eb10-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="4eb10-365">System.Xml</span></span>

| <span data-ttu-id="4eb10-366">成員</span><span class="sxs-lookup"><span data-stu-id="4eb10-366">Member</span></span> | <span data-ttu-id="4eb10-367">擲回的平臺</span><span class="sxs-lookup"><span data-stu-id="4eb10-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-368">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-369">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="4eb10-370">全部</span><span class="sxs-lookup"><span data-stu-id="4eb10-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="4eb10-371">請參閱</span><span class="sxs-lookup"><span data-stu-id="4eb10-371">See also</span></span>

- [<span data-ttu-id="4eb10-372">從 .NET Framework 遷移至 .NET Core 的突破性變更</span><span class="sxs-lookup"><span data-stu-id="4eb10-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="4eb10-373">.NET Core 中的二進位序列化</span><span class="sxs-lookup"><span data-stu-id="4eb10-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="4eb10-374">.NET 可攜性分析器</span><span class="sxs-lookup"><span data-stu-id="4eb10-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
