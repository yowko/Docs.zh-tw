---
title: .NET 中的 COM Interop
description: 了解如何在 .NET 中與 COM 程式庫交互操作。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 07/11/2019
ms.openlocfilehash: 9355e2ae84da623ffa725f5b2ac1bdee25b966d8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971885"
---
# <a name="com-interop-in-net"></a><span data-ttu-id="74d82-103">.NET 中的 COM Interop</span><span class="sxs-lookup"><span data-stu-id="74d82-103">COM Interop in .NET</span></span>

<span data-ttu-id="74d82-104">元件物件模型 (COM) 可讓物件向其他元件公開其功能並在 Windows 平台上主控應用程式。</span><span class="sxs-lookup"><span data-stu-id="74d82-104">The Component Object Model (COM) lets an object expose its functionality to other components and to host applications on Windows platforms.</span></span> <span data-ttu-id="74d82-105">為了協助使用者與現有的程式碼基底交互操作，.NET Framework 一律提供對於與 COM 程式庫交互操作的強大支援。</span><span class="sxs-lookup"><span data-stu-id="74d82-105">To help enable users to interoperate with their existing code bases, the .NET Framework has always provided strong support for interoperating with COM libraries.</span></span> <span data-ttu-id="74d82-106">在 .NET Core 3.0 中，這項支援的一大部分已新增至 Windows 上的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="74d82-106">In .NET Core 3.0, a large portion of this support has been added to .NET Core on Windows.</span></span> <span data-ttu-id="74d82-107">這裡的文件將說明常見的 COM Interop 技術如何運作，以及如何利用它們來與現有的 COM 程式庫交互操作。</span><span class="sxs-lookup"><span data-stu-id="74d82-107">The documentation here will explain how the common COM interop techonologies work and how you can utilize them to interoperate with your existing COM libraries.</span></span>

- [<span data-ttu-id="74d82-108">COM 包裝函式</span><span class="sxs-lookup"><span data-stu-id="74d82-108">COM Wrappers</span></span>](./com-wrappers.md)
- [<span data-ttu-id="74d82-109">COM 可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="74d82-109">COM Callable Wrappers</span></span>](./com-callable-wrapper.md)
- [<span data-ttu-id="74d82-110">執行階段可呼叫的包裝函式</span><span class="sxs-lookup"><span data-stu-id="74d82-110">Runtime Callable Wrappers</span></span>](./runtime-callable-wrapper.md)
- [<span data-ttu-id="74d82-111">限定 COM 交互操作的 .NET 型別</span><span class="sxs-lookup"><span data-stu-id="74d82-111">Qualifying .NET Types for COM Interoperation</span></span>](./qualify-net-types-for-interoperation.md)
