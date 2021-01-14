---
title: NETSDK1059：專案包含過時的 .NET CLI 工具
description: 如何解決包含過時 .NET CLI 工具之專案的問題。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1059
ms.openlocfilehash: bba5f4dafa346d81274541f3c40ecc5ed6fff8ab
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190321"
---
# <a name="netsdk1059-project-contains-obsolete-net-cli-tool"></a><span data-ttu-id="6ee56-103">NETSDK1059：專案包含過時的 .NET CLI 工具</span><span class="sxs-lookup"><span data-stu-id="6ee56-103">NETSDK1059: Project contains obsolete .NET CLI tool</span></span>

<span data-ttu-id="6ee56-104">本文 **適用于：** ✔️ .net CORE 2.1.100 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="6ee56-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="6ee56-105">當 .NET SDK 發出警告 NETSDK1059 時，您的專案會包含過時的 .NET CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="6ee56-105">When the .NET SDK issues warning NETSDK1059, your project contains an obsolete .NET CLI tool.</span></span> <span data-ttu-id="6ee56-106">從 .NET Core 2.1，這些工具都包含在 .NET SDK 中，而且不需要由專案明確參考。</span><span class="sxs-lookup"><span data-stu-id="6ee56-106">As of .NET Core 2.1, these tools are included in the .NET SDK and do not need to be explicitly referenced by the project.</span></span> <span data-ttu-id="6ee56-107">如需遷移至 .NET Core 2.1 的詳細資訊，請參閱 [這裡](../../migration/20-21.md)。</span><span class="sxs-lookup"><span data-stu-id="6ee56-107">More information for migrating to .NET Core 2.1 can be found [here](../../migration/20-21.md).</span></span>
