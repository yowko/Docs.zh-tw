---
title: SoundPlayer 類別概觀
ms.date: 03/30/2017
helpviewer_keywords:
- playing sounds [Windows Forms], SoundPlayer class
- SoundPlayer class [Windows Forms], about SoundPlayer class
- sounds [Windows Forms], playing
ms.assetid: fcebb938-62b9-4677-9cbe-6465bc863e22
ms.openlocfilehash: 3ff23cbfa78b803d4526e7a7c389fd5d458a967c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195003"
---
# <a name="soundplayer-class-overview"></a><span data-ttu-id="2d6b5-102">SoundPlayer 類別概觀</span><span class="sxs-lookup"><span data-stu-id="2d6b5-102">SoundPlayer Class Overview</span></span>
<span data-ttu-id="2d6b5-103"><xref:System.Media.SoundPlayer> 類別可讓您輕鬆地在應用程式中包含音效。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-103">The <xref:System.Media.SoundPlayer> class enables you to easily include sounds in your applications.</span></span>  
  
 <span data-ttu-id="2d6b5-104"><xref:System.Media.SoundPlayer>類別可以播放.wav 格式，從資源或者從 UNC 或 HTTP 位置中的音效檔。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-104">The <xref:System.Media.SoundPlayer> class can play sound files in the .wav format, either from a resource or from UNC or HTTP locations.</span></span> <span data-ttu-id="2d6b5-105">此外，<xref:System.Media.SoundPlayer>類別可讓您載入或以非同步方式播放音效。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-105">Additionally, the <xref:System.Media.SoundPlayer> class enables you to load or play sounds asynchronously.</span></span>  
  
 <span data-ttu-id="2d6b5-106">您也可以使用 <xref:System.Media.SystemSounds> 類別來播放常見的系統音效，包括嗶聲。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-106">You can also use the <xref:System.Media.SystemSounds> class to play common system sounds, including a beep.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="2d6b5-107">常用屬性、方法和事件</span><span class="sxs-lookup"><span data-stu-id="2d6b5-107">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="2d6b5-108">名稱</span><span class="sxs-lookup"><span data-stu-id="2d6b5-108">Name</span></span>|<span data-ttu-id="2d6b5-109">描述</span><span class="sxs-lookup"><span data-stu-id="2d6b5-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="2d6b5-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="2d6b5-110"><xref:System.Media.SoundPlayer.SoundLocation%2A> property</span></span>|<span data-ttu-id="2d6b5-111">音效的檔案路徑或網址。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-111">The file path or Web address of the sound.</span></span> <span data-ttu-id="2d6b5-112">可接受的值可以是 UNC 或 HTTP。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-112">Acceptable values can be UNC or HTTP.</span></span>|  
|<span data-ttu-id="2d6b5-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="2d6b5-113"><xref:System.Media.SoundPlayer.LoadTimeout%2A> property</span></span>|<span data-ttu-id="2d6b5-114">程式在擲回例外狀況之前等待載入音效的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-114">The number of milliseconds your program will wait to load a sound before it throws an exception.</span></span> <span data-ttu-id="2d6b5-115">預設為 10 秒。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-115">The default is 10 seconds.</span></span>|  
|<span data-ttu-id="2d6b5-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="2d6b5-116"><xref:System.Media.SoundPlayer.IsLoadCompleted%2A> property</span></span>|<span data-ttu-id="2d6b5-117">表示音效是否完成載入的布林值。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-117">A Boolean value indicating whether the sound has finished loading.</span></span>|  
|<span data-ttu-id="2d6b5-118"><xref:System.Media.SoundPlayer.Load%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="2d6b5-118"><xref:System.Media.SoundPlayer.Load%2A> method</span></span>|<span data-ttu-id="2d6b5-119">同步載入音效。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-119">Loads a sound synchronously.</span></span>|  
|<span data-ttu-id="2d6b5-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="2d6b5-120"><xref:System.Media.SoundPlayer.LoadAsync%2A> method</span></span>|<span data-ttu-id="2d6b5-121">開始非同步載入音效。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-121">Begins to load a sound asynchronously.</span></span> <span data-ttu-id="2d6b5-122">載入完成時，便會產生<xref:System.Media.SoundPlayer.OnLoadCompleted%2A>事件。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-122">When loading is complete, it raises the <xref:System.Media.SoundPlayer.OnLoadCompleted%2A> event.</span></span>|  
|<span data-ttu-id="2d6b5-123"><xref:System.Media.SoundPlayer.Play%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="2d6b5-123"><xref:System.Media.SoundPlayer.Play%2A> method</span></span>|<span data-ttu-id="2d6b5-124">扮演指定的音效<xref:System.Media.SoundPlayer.SoundLocation%2A>或<xref:System.Media.SoundPlayer.Stream%2A>中新的執行緒屬性。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-124">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in a new thread.</span></span>|  
|<span data-ttu-id="2d6b5-125"><xref:System.Media.SoundPlayer.PlaySync%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="2d6b5-125"><xref:System.Media.SoundPlayer.PlaySync%2A> method</span></span>|<span data-ttu-id="2d6b5-126">扮演指定的音效<xref:System.Media.SoundPlayer.SoundLocation%2A>或<xref:System.Media.SoundPlayer.Stream%2A>目前執行緒中的屬性。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-126">Plays the sound specified in the <xref:System.Media.SoundPlayer.SoundLocation%2A> or <xref:System.Media.SoundPlayer.Stream%2A> property in the current thread.</span></span>|  
|<span data-ttu-id="2d6b5-127"><xref:System.Media.SoundPlayer.Stop%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="2d6b5-127"><xref:System.Media.SoundPlayer.Stop%2A> method</span></span>|<span data-ttu-id="2d6b5-128">停止任何目前正在播放的音效。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-128">Stops any sound currently playing.</span></span>|  
|<span data-ttu-id="2d6b5-129"><xref:System.Media.SoundPlayer.LoadCompleted> 事件</span><span class="sxs-lookup"><span data-stu-id="2d6b5-129"><xref:System.Media.SoundPlayer.LoadCompleted> event</span></span>|<span data-ttu-id="2d6b5-130">在嘗試載入音效之後引發。</span><span class="sxs-lookup"><span data-stu-id="2d6b5-130">Raised after the load of a sound is attempted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d6b5-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d6b5-131">See also</span></span>

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
