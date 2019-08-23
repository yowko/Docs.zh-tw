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
ms.openlocfilehash: 61ee38319b2f0aa46690fb063f6ffe6612f993ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918439"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="a748d-102">HOW TO：在 XAML 中使用特殊字元</span><span class="sxs-lookup"><span data-stu-id="a748d-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="a748d-103">在中[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]建立的標記檔案會自動儲存[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]為 utf-8 檔案格式, 這表示大部分的特殊字元 (例如重音標記) 都會正確編碼。</span><span class="sxs-lookup"><span data-stu-id="a748d-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="a748d-104">不過，有一組常用的特殊字元則採用不同的處理方式。</span><span class="sxs-lookup"><span data-stu-id="a748d-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="a748d-105">這些特殊字元會遵循[!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)]標準進行編碼。</span><span class="sxs-lookup"><span data-stu-id="a748d-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="a748d-106">下表顯示這組特殊字元的編碼語法：</span><span class="sxs-lookup"><span data-stu-id="a748d-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="a748d-107">字元</span><span class="sxs-lookup"><span data-stu-id="a748d-107">Character</span></span>|<span data-ttu-id="a748d-108">語法</span><span class="sxs-lookup"><span data-stu-id="a748d-108">Syntax</span></span>|<span data-ttu-id="a748d-109">說明</span><span class="sxs-lookup"><span data-stu-id="a748d-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="a748d-110">小於符號。</span><span class="sxs-lookup"><span data-stu-id="a748d-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="a748d-111">大於符號。</span><span class="sxs-lookup"><span data-stu-id="a748d-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="a748d-112">& 符號。</span><span class="sxs-lookup"><span data-stu-id="a748d-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="a748d-113">"</span><span class="sxs-lookup"><span data-stu-id="a748d-113">"</span></span>|`&quot;`|<span data-ttu-id="a748d-114">雙引號。</span><span class="sxs-lookup"><span data-stu-id="a748d-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a748d-115">如果您使用文字編輯器 (例如 Windows 記事本) 來建立標記檔案, 就必須以[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] utf-8 檔案格式儲存檔案, 才能保留任何編碼的特殊字元。</span><span class="sxs-lookup"><span data-stu-id="a748d-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="a748d-116">下列範例示範如何在建立標記時，於文字中使用特殊字元。</span><span class="sxs-lookup"><span data-stu-id="a748d-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a748d-117">範例</span><span class="sxs-lookup"><span data-stu-id="a748d-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
