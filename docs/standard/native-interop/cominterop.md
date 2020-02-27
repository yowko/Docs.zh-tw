---
title: .NET 中的 COM Interop
description: 了解如何在 .NET 中與 COM 程式庫交互操作。
ms.date: 07/11/2019
ms.openlocfilehash: 63205ae5c09d6c3929da13788eb781cd975ca814
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627370"
---
# <a name="com-interop-in-net"></a><span data-ttu-id="830f9-103">.NET 中的 COM Interop</span><span class="sxs-lookup"><span data-stu-id="830f9-103">COM Interop in .NET</span></span>

<span data-ttu-id="830f9-104">元件物件模型 (COM) 可讓物件向其他元件公開其功能並在 Windows 平台上主控應用程式。</span><span class="sxs-lookup"><span data-stu-id="830f9-104">The Component Object Model (COM) lets an object expose its functionality to other components and to host applications on Windows platforms.</span></span> <span data-ttu-id="830f9-105">為了協助使用者與現有的程式碼基底交互操作，.NET Framework 一律提供對於與 COM 程式庫交互操作的強大支援。</span><span class="sxs-lookup"><span data-stu-id="830f9-105">To help enable users to interoperate with their existing code bases, the .NET Framework has always provided strong support for interoperating with COM libraries.</span></span> <span data-ttu-id="830f9-106">在 .NET Core 3.0 中，這項支援的一大部分已新增至 Windows 上的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="830f9-106">In .NET Core 3.0, a large portion of this support has been added to .NET Core on Windows.</span></span> <span data-ttu-id="830f9-107">這裡的檔將說明常見的 COM Interop 技術如何運作，以及如何利用它們來與您現有的 COM 程式庫交互操作。</span><span class="sxs-lookup"><span data-stu-id="830f9-107">The documentation here will explain how the common COM interop technologies work and how you can utilize them to interoperate with your existing COM libraries.</span></span>

- [<span data-ttu-id="830f9-108">COM 包裝函式</span><span class="sxs-lookup"><span data-stu-id="830f9-108">COM Wrappers</span></span>](./com-wrappers.md)
- [<span data-ttu-id="830f9-109">COM 可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="830f9-109">COM Callable Wrappers</span></span>](./com-callable-wrapper.md)
- [<span data-ttu-id="830f9-110">執行階段可呼叫的包裝函式</span><span class="sxs-lookup"><span data-stu-id="830f9-110">Runtime Callable Wrappers</span></span>](./runtime-callable-wrapper.md)
- [<span data-ttu-id="830f9-111">限定 COM 交互操作的 .NET 型別</span><span class="sxs-lookup"><span data-stu-id="830f9-111">Qualifying .NET Types for COM Interoperation</span></span>](./qualify-net-types-for-interoperation.md)
