---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234131"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="d423d-101">若語言不在 OS 的輸入語言清單中，啟用文字之控制項中的　WPF 拼字檢查不適用於 Windows 10</span><span class="sxs-lookup"><span data-stu-id="d423d-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d423d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d423d-102">Details</span></span>|<span data-ttu-id="d423d-103">因為只有輸入語言清單上的語言可以使用平台拼字檢查功能，所以拼字檢查工具在 Windows 10 上執行時可能不適用於啟用 WPF 文字的控制項。在 Windows 10 中，將語言新增至可用鍵盤的清單時，Windows 會自動下載並安裝對應的 Feature on Demand (FOD) 套件，以提供拼字檢查功能。</span><span class="sxs-lookup"><span data-stu-id="d423d-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="d423d-104">只要將語言加入輸入語言清單中，就可支援拼字檢查工具。</span><span class="sxs-lookup"><span data-stu-id="d423d-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>|
|<span data-ttu-id="d423d-105">建議</span><span class="sxs-lookup"><span data-stu-id="d423d-105">Suggestion</span></span>|<span data-ttu-id="d423d-106">請注意，要進行拼字檢查的語言或文字必須新增為輸入語言，拼字檢查才能在 Windows 10 中正常運作。</span><span class="sxs-lookup"><span data-stu-id="d423d-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>|
|<span data-ttu-id="d423d-107">範圍</span><span class="sxs-lookup"><span data-stu-id="d423d-107">Scope</span></span>|<span data-ttu-id="d423d-108">Edge</span><span class="sxs-lookup"><span data-stu-id="d423d-108">Edge</span></span>|
|<span data-ttu-id="d423d-109">版本</span><span class="sxs-lookup"><span data-stu-id="d423d-109">Version</span></span>|<span data-ttu-id="d423d-110">4.6</span><span class="sxs-lookup"><span data-stu-id="d423d-110">4.6</span></span>|
|<span data-ttu-id="d423d-111">類型</span><span class="sxs-lookup"><span data-stu-id="d423d-111">Type</span></span>|<span data-ttu-id="d423d-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="d423d-112">Runtime</span></span>|
