---
title: NETSDK1005 和 NETSDK1047：資產檔案遺失目標
description: 如何解決資產檔案遺失目標的問題。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 6c22fd8c79c2ac6e024b46b4f67e08011d42efc6
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957140"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="cad82-103">NETSDK1005 和 NETSDK1047：資產檔案遺失目標</span><span class="sxs-lookup"><span data-stu-id="cad82-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="cad82-104">本文**適用于：** ✔️ .NET 2.1.100 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="cad82-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="cad82-105">當 .NET SDK 發出錯誤 NETSDK1005 或 NETSDK1047 時，專案的資產檔案就會遺失其中一個目標 framework 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cad82-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="cad82-106">通常可以藉由確保執行還原，而遺漏的目標值包含在專案的屬性中，來修正此問題 `TargetFrameworks` 。</span><span class="sxs-lookup"><span data-stu-id="cad82-106">This can usually be fixed by ensuring that restore is run and that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>

> [!NOTE]
> <span data-ttu-id="cad82-107">當 .NET 5 preview 8 的早期版本搭配使用時，有一個已知的問題，就是與導致此錯誤的 Visual Studio 16.8 預覽版本搭配使用。</span><span class="sxs-lookup"><span data-stu-id="cad82-107">There was a known issue with early builds of .NET 5 preview 8 when used with versions of Visual Studio 16.8 previews which resulted in this error.</span></span> <span data-ttu-id="cad82-108">具體而言，如果遺漏的目標是 `net5.0-windows7.0` 或 `net5.0` ，請確定您已更新為最新版本的 Visual Studio 和 .NET 5 SDK。</span><span class="sxs-lookup"><span data-stu-id="cad82-108">Specifically, if the missing target is `net5.0-windows7.0` or `net5.0`, ensure that you have updated to the latest versions of Visual Studio and the .NET 5 SDK.</span></span>
