---
description: -preferreduilang (C# 編譯器選項)
title: -preferreduilang (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: f68652e910651ab5c4184376d9eb7729303382d9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124847"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="a1a3d-103">-preferreduilang (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="a1a3d-103">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="a1a3d-104">使用 `-preferreduilang` 編譯器選項，您就可以指定 C# 編譯器顯示輸出的語言，例如錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a1a3d-104">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1a3d-105">語法</span><span class="sxs-lookup"><span data-stu-id="a1a3d-105">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="a1a3d-106">引數</span><span class="sxs-lookup"><span data-stu-id="a1a3d-106">Arguments</span></span>  
 `language`  
 <span data-ttu-id="a1a3d-107">編譯器輸出所用語言的[語言名稱](/windows/desktop/Intl/language-names)。</span><span class="sxs-lookup"><span data-stu-id="a1a3d-107">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1a3d-108">備註</span><span class="sxs-lookup"><span data-stu-id="a1a3d-108">Remarks</span></span>  
 <span data-ttu-id="a1a3d-109">您可以使用 `-preferreduilang` 編譯器選項指定 C# 編譯器要用於錯誤訊息和其他命令列輸出的語言。</span><span class="sxs-lookup"><span data-stu-id="a1a3d-109">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="a1a3d-110">如果尚未安裝此語言的語言套件，則會改用作業系統的語言設定，而且不會回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="a1a3d-110">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="a1a3d-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="a1a3d-111">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a3d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1a3d-112">See also</span></span>

- [<span data-ttu-id="a1a3d-113">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="a1a3d-113">C# Compiler Options</span></span>](./index.md)
