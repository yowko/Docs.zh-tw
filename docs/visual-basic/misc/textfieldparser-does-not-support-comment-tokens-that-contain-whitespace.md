---
title: TextFieldParser 不支援包含空白字元的註解標記
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 51dc2b82d7f04c652e18173b8450b65c15ee6ec2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411892"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a><span data-ttu-id="d991f-102">TextFieldParser 不支援包含空白字元的註解標記</span><span class="sxs-lookup"><span data-stu-id="d991f-102">TextFieldParser does not support comment tokens that contain white space</span></span>
<span data-ttu-id="d991f-103">已提供包含空白字元的註解語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d991f-103">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="d991f-104">`TextFieldParser` 不支援包含空白字元的註解語彙基元，除非空白字元發生在語彙基元的開頭。</span><span class="sxs-lookup"><span data-stu-id="d991f-104">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="d991f-105">發生在語彙基元開頭的空白字元會被忽略。</span><span class="sxs-lookup"><span data-stu-id="d991f-105">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d991f-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d991f-106">To correct this error</span></span>  
  
- <span data-ttu-id="d991f-107">請提供正確的註解語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d991f-107">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d991f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d991f-108">See also</span></span>

- [<span data-ttu-id="d991f-109">TextFieldParser.CommentTokens 屬性</span><span class="sxs-lookup"><span data-stu-id="d991f-109">TextFieldParser.CommentTokens Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [<span data-ttu-id="d991f-110">使用 TextFieldParser 物件剖析文字檔</span><span class="sxs-lookup"><span data-stu-id="d991f-110">Parsing Text Files with the TextFieldParser Object</span></span>](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="d991f-111">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="d991f-111">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
