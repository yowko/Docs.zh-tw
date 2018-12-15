---
title: dotnet list reference 命令 - .NET Core CLI
description: dotnet list reference 命令提供方便的選項，以列出專案對專案參考。
ms.date: 12/03/2018
ms.openlocfilehash: 58b4e07abfe95d1febdd54d117825ecedf502e61
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152591"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="3410c-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="3410c-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3410c-104">名稱</span><span class="sxs-lookup"><span data-stu-id="3410c-104">Name</span></span>

<span data-ttu-id="3410c-105">`dotnet list reference` - 列出專案對專案參考。</span><span class="sxs-lookup"><span data-stu-id="3410c-105">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3410c-106">概要</span><span class="sxs-lookup"><span data-stu-id="3410c-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="3410c-107">說明</span><span class="sxs-lookup"><span data-stu-id="3410c-107">Description</span></span>

<span data-ttu-id="3410c-108">`dotnet list reference` 命令提供一個列出指定專案或解決方案之專案參考的便利選項。</span><span class="sxs-lookup"><span data-stu-id="3410c-108">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="3410c-109">引數</span><span class="sxs-lookup"><span data-stu-id="3410c-109">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="3410c-110">指定要用於列出參考的專案檔。</span><span class="sxs-lookup"><span data-stu-id="3410c-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="3410c-111">如果未指定，命令會在目前的目錄中搜尋專案檔。</span><span class="sxs-lookup"><span data-stu-id="3410c-111">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="3410c-112">選項</span><span class="sxs-lookup"><span data-stu-id="3410c-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="3410c-113">印出命令的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="3410c-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="3410c-114">範例</span><span class="sxs-lookup"><span data-stu-id="3410c-114">Examples</span></span>

* <span data-ttu-id="3410c-115">列出指定專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="3410c-115">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="3410c-116">列出目前目錄中專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="3410c-116">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```