---
title: 變數使用不支援的 Automation 類型
ms.date: 07/20/2015
f1_keywords:
- vbrID458
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
ms.openlocfilehash: 944c0c63cd0d7ae7f9ff770fd123231464af1eaf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344834"
---
# <a name="variable-uses-an-automation-type-not-supported-in-visual-basic"></a><span data-ttu-id="2a64b-102">變數使用在 Visual Basic 中不支援的 Automation 類型</span><span class="sxs-lookup"><span data-stu-id="2a64b-102">Variable uses an Automation type not supported in Visual Basic</span></span>

<span data-ttu-id="2a64b-103">您嘗試使用類型程式庫或物件程式庫中所定義的變數，但其具有 Visual Basic 不支援的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2a64b-103">You tried to use a variable defined in a type library or object library that has a data type not supported by Visual Basic.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2a64b-104">若要改正這項錯誤</span><span class="sxs-lookup"><span data-stu-id="2a64b-104">To correct this error</span></span>

- <span data-ttu-id="2a64b-105">使用 Visual Basic 所識別之類型的變數。</span><span class="sxs-lookup"><span data-stu-id="2a64b-105">Use a variable of a type recognized by Visual Basic.</span></span>

     <span data-ttu-id="2a64b-106">-或-</span><span class="sxs-lookup"><span data-stu-id="2a64b-106">-or-</span></span>

- <span data-ttu-id="2a64b-107">如果您在使用 `FileGet` 或 `FileGetObject`時遇到此錯誤，請確定您嘗試使用的檔案已寫入 `FilePut` 或 `FilePutObject`。</span><span class="sxs-lookup"><span data-stu-id="2a64b-107">If you encounter this error while using `FileGet` or `FileGetObject`, make sure the file you are trying to use was written to with `FilePut` or `FilePutObject`.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a64b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a64b-108">See also</span></span>

- [<span data-ttu-id="2a64b-109">資料類型</span><span class="sxs-lookup"><span data-stu-id="2a64b-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
