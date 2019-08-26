---
title: -preferreduilang (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 7ebafcf446c9033c93e0c5fa5e11ea2930bd2e1e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602554"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="4330d-102">-preferreduilang (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="4330d-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="4330d-103">使用 `-preferreduilang` 編譯器選項，您就可以指定 C# 編譯器顯示輸出的語言，例如錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4330d-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4330d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4330d-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="4330d-105">引數</span><span class="sxs-lookup"><span data-stu-id="4330d-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="4330d-106">編譯器輸出所用語言的[語言名稱](/windows/desktop/Intl/language-names)。</span><span class="sxs-lookup"><span data-stu-id="4330d-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4330d-107">備註</span><span class="sxs-lookup"><span data-stu-id="4330d-107">Remarks</span></span>  
 <span data-ttu-id="4330d-108">您可以使用 `-preferreduilang` 編譯器選項指定 C# 編譯器要用於錯誤訊息和其他命令列輸出的語言。</span><span class="sxs-lookup"><span data-stu-id="4330d-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="4330d-109">如果尚未安裝此語言的語言套件，則會改用作業系統的語言設定，而且不會回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="4330d-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="4330d-110">需求</span><span class="sxs-lookup"><span data-stu-id="4330d-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4330d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4330d-111">See also</span></span>

- [<span data-ttu-id="4330d-112">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="4330d-112">C# Compiler Options</span></span>](./index.md)
