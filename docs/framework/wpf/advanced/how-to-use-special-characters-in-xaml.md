---
title: 如何：在 XAML 中使用特殊字元
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 59449637bb45f6b75462b6809c354af7972fc2e7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740838"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="e1ca9-102">如何：在 XAML 中使用特殊字元</span><span class="sxs-lookup"><span data-stu-id="e1ca9-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="e1ca9-103">在 Visual Studio 中建立的標記檔會自動以 Unicode UTF-8 檔案格式儲存，這表示大部分的特殊字元（例如重音標記）都會正確編碼。</span><span class="sxs-lookup"><span data-stu-id="e1ca9-103">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="e1ca9-104">不過，有一組常用的特殊字元則採用不同的處理方式。</span><span class="sxs-lookup"><span data-stu-id="e1ca9-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="e1ca9-105">這些特殊字元遵循全球資訊網協會（W3C） XML 標準進行編碼。</span><span class="sxs-lookup"><span data-stu-id="e1ca9-105">These special characters follow the World Wide Web Consortium (W3C) XML standard for encoding.</span></span>  
  
 <span data-ttu-id="e1ca9-106">下表顯示這組特殊字元的編碼語法：</span><span class="sxs-lookup"><span data-stu-id="e1ca9-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="e1ca9-107">字元</span><span class="sxs-lookup"><span data-stu-id="e1ca9-107">Character</span></span>|<span data-ttu-id="e1ca9-108">語法</span><span class="sxs-lookup"><span data-stu-id="e1ca9-108">Syntax</span></span>|<span data-ttu-id="e1ca9-109">描述</span><span class="sxs-lookup"><span data-stu-id="e1ca9-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="e1ca9-110">小於符號。</span><span class="sxs-lookup"><span data-stu-id="e1ca9-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="e1ca9-111">大於符號。</span><span class="sxs-lookup"><span data-stu-id="e1ca9-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="e1ca9-112">& 符號。</span><span class="sxs-lookup"><span data-stu-id="e1ca9-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="e1ca9-113">"</span><span class="sxs-lookup"><span data-stu-id="e1ca9-113">"</span></span>|`&quot;`|<span data-ttu-id="e1ca9-114">雙引號。</span><span class="sxs-lookup"><span data-stu-id="e1ca9-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e1ca9-115">如果您使用文字編輯器（例如 Windows 記事本）來建立標記檔案，就必須以 Unicode UTF-8 檔案格式儲存檔案，才能保留任何編碼的特殊字元。</span><span class="sxs-lookup"><span data-stu-id="e1ca9-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="e1ca9-116">下列範例示範如何在建立標記時，於文字中使用特殊字元。</span><span class="sxs-lookup"><span data-stu-id="e1ca9-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1ca9-117">範例</span><span class="sxs-lookup"><span data-stu-id="e1ca9-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
