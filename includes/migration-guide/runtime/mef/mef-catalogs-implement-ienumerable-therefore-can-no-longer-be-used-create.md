---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235162"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="e0c35-101">MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式</span><span class="sxs-lookup"><span data-stu-id="e0c35-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e0c35-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e0c35-102">Details</span></span>|<span data-ttu-id="e0c35-103">從 .NET Framework 4.5 開始，MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式 (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> 物件)。</span><span class="sxs-lookup"><span data-stu-id="e0c35-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> object).</span></span> <span data-ttu-id="e0c35-104">嘗試序列化 MEF 目錄會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e0c35-104">Trying to serialize a MEF catalog throws an exception.</span></span>|
|<span data-ttu-id="e0c35-105">建議</span><span class="sxs-lookup"><span data-stu-id="e0c35-105">Suggestion</span></span>|<span data-ttu-id="e0c35-106">無法再使用 MEF 建立序列化程式</span><span class="sxs-lookup"><span data-stu-id="e0c35-106">Can no longer use MEF to create a serializer</span></span>|
|<span data-ttu-id="e0c35-107">範圍</span><span class="sxs-lookup"><span data-stu-id="e0c35-107">Scope</span></span>|<span data-ttu-id="e0c35-108">主要</span><span class="sxs-lookup"><span data-stu-id="e0c35-108">Major</span></span>|
|<span data-ttu-id="e0c35-109">版本</span><span class="sxs-lookup"><span data-stu-id="e0c35-109">Version</span></span>|<span data-ttu-id="e0c35-110">4.5</span><span class="sxs-lookup"><span data-stu-id="e0c35-110">4.5</span></span>|
|<span data-ttu-id="e0c35-111">類型</span><span class="sxs-lookup"><span data-stu-id="e0c35-111">Type</span></span>|<span data-ttu-id="e0c35-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="e0c35-112">Runtime</span></span>|
