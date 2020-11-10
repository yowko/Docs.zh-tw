---
title: NETSDK1022：包含重複的專案。
description: 如何根據預設包含來解析重複專案訊息。
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: 46c3d7d451e7c9e5b456b6e4e45054c3a4844386
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445760"
---
# <a name="netsdk1022-duplicate-items-were-included"></a><span data-ttu-id="757f1-103">NETSDK1022：包含重複的專案。</span><span class="sxs-lookup"><span data-stu-id="757f1-103">NETSDK1022: Duplicate items were included.</span></span>

<span data-ttu-id="757f1-104">本文 **適用于：** ✔️ .NET 2.1.100 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="757f1-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="757f1-105">從 Visual Studio 15.3 開始，.NET SDK 預設會自動從專案目錄中包含專案。</span><span class="sxs-lookup"><span data-stu-id="757f1-105">Starting in Visual Studio 15.3, the .NET SDK automatically includes items from the project directory by default.</span></span>  <span data-ttu-id="757f1-106">這包括 `Compile` 和 `Content` 目標。</span><span class="sxs-lookup"><span data-stu-id="757f1-106">This includes `Compile` and `Content` targets.</span></span>  <span data-ttu-id="757f1-107">這應該會大幅清除您的專案檔，並降低您在該處的複雜度。</span><span class="sxs-lookup"><span data-stu-id="757f1-107">This should greatly clean up your project file and reduce the complexity you have there.</span></span>

<span data-ttu-id="757f1-108">您可以藉由將正確的屬性設定為 false，來還原為先前的行為。</span><span class="sxs-lookup"><span data-stu-id="757f1-108">You can revert to the earlier behavior by setting the correct property to false.</span></span>

<span data-ttu-id="757f1-109">專案範例 `Compile` ：</span><span class="sxs-lookup"><span data-stu-id="757f1-109">Example for `Compile` items:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
