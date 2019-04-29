---
title: TextFieldParser 不支援包含空白字元的註解語彙基元
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 9a14bc29ecfa917b6213f32cd170aa83d6f60f58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668987"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a><span data-ttu-id="b7103-102">TextFieldParser 不支援包含空白字元的註解語彙基元</span><span class="sxs-lookup"><span data-stu-id="b7103-102">TextFieldParser does not support comment tokens that contain white space</span></span>
<span data-ttu-id="b7103-103">已提供包含空白字元的註解語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b7103-103">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="b7103-104">`TextFieldParser` 不支援包含空白字元的註解語彙基元，除非空白字元發生在語彙基元的開頭。</span><span class="sxs-lookup"><span data-stu-id="b7103-104">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="b7103-105">發生在語彙基元開頭的空白字元會被忽略。</span><span class="sxs-lookup"><span data-stu-id="b7103-105">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b7103-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b7103-106">To correct this error</span></span>  
  
- <span data-ttu-id="b7103-107">請提供正確的註解語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b7103-107">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7103-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7103-108">See also</span></span>

- [<span data-ttu-id="b7103-109">TextFieldParser.CommentTokens 屬性</span><span class="sxs-lookup"><span data-stu-id="b7103-109">TextFieldParser.CommentTokens Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [<span data-ttu-id="b7103-110">使用 TextFieldParser 物件剖析文字檔</span><span class="sxs-lookup"><span data-stu-id="b7103-110">Parsing Text Files with the TextFieldParser Object</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="b7103-111">TextFieldParser 物件</span><span class="sxs-lookup"><span data-stu-id="b7103-111">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
