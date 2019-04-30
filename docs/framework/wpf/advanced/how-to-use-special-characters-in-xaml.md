---
title: HOW TO：在 XAML 中使用特殊字元
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 18934e06f45ca4b88f48bce8a310a07b460a5f53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051076"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="e2fdd-102">HOW TO：在 XAML 中使用特殊字元</span><span class="sxs-lookup"><span data-stu-id="e2fdd-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="e2fdd-103">標記檔案中建立[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]會自動儲存在[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]utf-8 檔案格式，這表示大部分的特殊字元，例如重音符號都會正確編碼。</span><span class="sxs-lookup"><span data-stu-id="e2fdd-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="e2fdd-104">不過，有一組常用的特殊字元則採用不同的處理方式。</span><span class="sxs-lookup"><span data-stu-id="e2fdd-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="e2fdd-105">這些特殊字元會遵循[!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)][!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)]標準進行編碼。</span><span class="sxs-lookup"><span data-stu-id="e2fdd-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="e2fdd-106">下表顯示這組特殊字元的編碼語法：</span><span class="sxs-lookup"><span data-stu-id="e2fdd-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="e2fdd-107">字元</span><span class="sxs-lookup"><span data-stu-id="e2fdd-107">Character</span></span>|<span data-ttu-id="e2fdd-108">語法</span><span class="sxs-lookup"><span data-stu-id="e2fdd-108">Syntax</span></span>|<span data-ttu-id="e2fdd-109">描述</span><span class="sxs-lookup"><span data-stu-id="e2fdd-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="e2fdd-110">小於符號。</span><span class="sxs-lookup"><span data-stu-id="e2fdd-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="e2fdd-111">大於符號。</span><span class="sxs-lookup"><span data-stu-id="e2fdd-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="e2fdd-112">& 符號。</span><span class="sxs-lookup"><span data-stu-id="e2fdd-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="e2fdd-113">"</span><span class="sxs-lookup"><span data-stu-id="e2fdd-113">"</span></span>|`&quot;`|<span data-ttu-id="e2fdd-114">雙引號。</span><span class="sxs-lookup"><span data-stu-id="e2fdd-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e2fdd-115">如果您建立標記檔案，使用文字編輯器，例如[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]「 記事本 」，您必須將檔案儲存在[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]utf-8 檔案格式，才能保留任何編碼的特殊字元。</span><span class="sxs-lookup"><span data-stu-id="e2fdd-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="e2fdd-116">下列範例示範如何在建立標記時，於文字中使用特殊字元。</span><span class="sxs-lookup"><span data-stu-id="e2fdd-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2fdd-117">範例</span><span class="sxs-lookup"><span data-stu-id="e2fdd-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
