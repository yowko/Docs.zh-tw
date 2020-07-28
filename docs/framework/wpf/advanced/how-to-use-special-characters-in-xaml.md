---
title: 如何：在 XAML 中使用特殊字元
description: 瞭解在 Visual Studio 中，以 Unicode UTF-8 檔案格式編碼特殊字元的語法，以便在 Windows Presentation Foundation 的 XAML 檔案中使用。
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: ac2388fd96aa26ddd99408ac9f847ce517958568
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168351"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="b60f6-103">如何：在 XAML 中使用特殊字元</span><span class="sxs-lookup"><span data-stu-id="b60f6-103">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="b60f6-104">在 Visual Studio 中建立的標記檔會自動以 Unicode UTF-8 檔案格式儲存，這表示大部分的特殊字元（例如重音標記）都會正確編碼。</span><span class="sxs-lookup"><span data-stu-id="b60f6-104">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="b60f6-105">不過，有一組常用的特殊字元則採用不同的處理方式。</span><span class="sxs-lookup"><span data-stu-id="b60f6-105">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="b60f6-106">這些特殊字元遵循全球資訊網協會（W3C） XML 標準進行編碼。</span><span class="sxs-lookup"><span data-stu-id="b60f6-106">These special characters follow the World Wide Web Consortium (W3C) XML standard for encoding.</span></span>  
  
 <span data-ttu-id="b60f6-107">下表顯示這組特殊字元的編碼語法：</span><span class="sxs-lookup"><span data-stu-id="b60f6-107">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="b60f6-108">字元</span><span class="sxs-lookup"><span data-stu-id="b60f6-108">Character</span></span>|<span data-ttu-id="b60f6-109">語法</span><span class="sxs-lookup"><span data-stu-id="b60f6-109">Syntax</span></span>|<span data-ttu-id="b60f6-110">描述</span><span class="sxs-lookup"><span data-stu-id="b60f6-110">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="b60f6-111">小於符號。</span><span class="sxs-lookup"><span data-stu-id="b60f6-111">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="b60f6-112">大於符號。</span><span class="sxs-lookup"><span data-stu-id="b60f6-112">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="b60f6-113">& 符號。</span><span class="sxs-lookup"><span data-stu-id="b60f6-113">Ampersand symbol.</span></span>|  
|<span data-ttu-id="b60f6-114">"</span><span class="sxs-lookup"><span data-stu-id="b60f6-114">"</span></span>|`&quot;`|<span data-ttu-id="b60f6-115">雙引號。</span><span class="sxs-lookup"><span data-stu-id="b60f6-115">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b60f6-116">如果您使用文字編輯器（例如 Windows 記事本）來建立標記檔案，就必須以 Unicode UTF-8 檔案格式儲存檔案，才能保留任何編碼的特殊字元。</span><span class="sxs-lookup"><span data-stu-id="b60f6-116">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="b60f6-117">下列範例示範如何在建立標記時，於文字中使用特殊字元。</span><span class="sxs-lookup"><span data-stu-id="b60f6-117">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b60f6-118">範例</span><span class="sxs-lookup"><span data-stu-id="b60f6-118">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
