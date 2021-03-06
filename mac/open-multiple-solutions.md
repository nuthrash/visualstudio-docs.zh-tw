---
title: HOW TO：在 Visual Studio for Mac 中開啟多個解決方案
description: 了解如何在 Visual Studio for Mac 中開啟多個方案，以及如何開啟應用程式的多個執行個體。
author: conceptdev
ms.author: crdun
ms.date: 04/02/2019
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.openlocfilehash: 031ce885faa29e587fe5d48210d8e13b48fcdc4c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62937944"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>開啟 Visual Studio for Mac 的多個方案或執行個體

根據預設，Mac 上的所有的應用程式 (包括 Visual Studio for Mac) 都是「單一執行個體」應用程式。 這表示，如果您想要使用的應用程式已開啟 (以 Dock 中圖示下的「點」表示)，再次選取該圖示會開啟執行中的執行個體，而不是新的執行個體。 如果您需要其他的應用程式執行個體，可以提示系統為您開啟它，如[下一節](#open-a-second-instance-of-visual-studio-for-mac)中所述。

此外，當您開啟方案時，預設行為是在新的工作區中開啟方案，並關閉目前的工作區 (如有必要)。 您可以將目前的工作區保持為開啟狀態，來覆寫這個預設行為，如[開啟第二個方案](#open-a-second-solution-inside-a-single-instance)一節中所述。

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>開啟 Visual Studio for Mac 的第二個執行個體

若要開啟整合式開發環境 (IDE) 的第二個執行個體，請以滑鼠右鍵按一下您固定位置中的 Visual Studio 圖示或 **Applications** 資料夾，然後選取 [新執行個體]。

![使用滑鼠右鍵按一下 Visual Studio 圖示之 [新執行個體] 功能表選項的螢幕擷取畫面](media/open-new-instance.png)

## <a name="open-a-second-solution-inside-a-single-instance"></a>在單一執行個體內開啟第二個方案

若要連同第一個解決方案開啟第二個方案，請使用下列步驟：

1. 第一個方案開啟之後，選取 [檔案] > [開啟]。
2. 瀏覽檔案系統，以尋找現有的解決方案。
3. 選取 **.sln** 檔案，然後選取 [選項]：

    ![Visual Studio for Mac 已反白顯示 .sln 檔案與 [選項] 的螢幕擷取畫面](media/open-multiple-solutions-image3.png)

4. 清除 [關閉目前的工作區] 方塊：

    ![[選項] 對話方塊已清除 [關閉目前的工作區] 的螢幕擷取畫面](media/open-multiple-solutions-image1.png)

5. 選取 [開啟] 以在 Solution Pad 中開啟第二個方案。

或者，如果您最近開啟了方案，則可以使用下列步驟：

1. 移至 [檔案] > [最近使用的方案]。

    ![[最近使用的方案] 功能表的螢幕擷取畫面](media/open-multiple-solutions-image2.png)

1. 按住 **Ctrl** 鍵並選取解決方案。 這個組合會在 Solution Pad 中開啟第二個方案。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
