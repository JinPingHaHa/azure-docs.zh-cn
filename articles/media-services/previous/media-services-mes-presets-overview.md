---
title: Media Encoder Standard (MES) 的任务预设 | Microsoft Docs
description: 本主题概述了 Media Encoder Standard (MES) 的服务定义示例预设。
author: Juliako
manager: femila
editor: johndeu
services: media-services
documentationcenter: ''
ms.assetid: f243ed1c-ac9c-4300-a5f7-f092cf9853b9
ms.service: media-services
ms.workload: media
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/09/2019
ms.author: juliako
ms.openlocfilehash: 9d32397773a5ede4ddc2a27c367f2750078e28c6
ms.sourcegitcommit: e69fc381852ce8615ee318b5f77ae7c6123a744c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2019
ms.locfileid: "55998092"
---
# <a name="sample-presets-for-media-encoder-standard-mes"></a>Media Encoder Standard (MES) 的示例预设

Media Encoder Standard 定义了一组可在创建编码作业时使用的预定义系统编码预设。 如果想要使用媒体服务对视频进行编码以实现流式处理，建议使用“自适应流式处理”预设。 指定此预设时，Media Encoder Standard 将[自动生成比特率阶梯](media-services-autogen-bitrate-ladder-with-mes.md)。 

### <a name="creating-custom-presets-from-samples"></a>从示例创建自定义预设
媒体服务完全支持自定义预设中的所有值，可满足特定的编码需求和要求。 如果需要自定义编码预设，应先采用此部分中提供的以下系统预设之一作为模板，以用于自定义配置。 有关这些预设中的每个元素的含义及其有效值的说明，请参阅 [Media Encoder Standard 架构](media-services-mes-schema.md)主题。  
  
> [!NOTE]
>  使用预设进行 4k 编码时，应获取 `S3` 预留单位类型。 有关详细信息，请参阅[如何缩放编码](https://azure.microsoft.com/documentation/articles/media-services-portal-encoding-units)。  

#### <a name="video-rotation-default-setting-in-presets"></a>预设中的视频旋转默认设置：
使用 Media Encoder Standard 时，默认启用视频旋转。 如果已在移动设备上采用纵向模式录制了视频，则在编码前，这些预设会将视频旋转为横向模式。
 
## <a name="available-presets"></a>可用预设： 

 [H264 多比特率 1080p Audio 5.1](media-services-mes-preset-H264-Multiple-Bitrate-1080p-Audio-5.1.md) 生成一组 8 GOP 对齐的 MP4 文件（范围从 6000 kbps 到 400 kbps）和 AAC 5.1 音频。  
  
 [H264 多比特率 1080p](media-services-mes-preset-H264-Multiple-Bitrate-1080p.md) 生成一组 8 GOP 对齐的 MP4 文件（范围从 6000 kbps 到 400 kbps）和立体声 AAC 音频。  
  
 [H264 多比特率 16x9 (iOS)](media-services-mes-preset-H264-Multiple-Bitrate-16x9-for-iOS.md) 生成一组 8 GOP 对齐的 MP4 文件（范围从 8500 kbps 到 200 kbps）和立体声 AAC 音频。  
  
 [H264 多比特率 16x9 SD Audio 5.1](media-services-mes-preset-H264-Multiple-Bitrate-16x9-SD-Audio-5.1.md) 生成一组 5 GOP 对齐的 MP4 文件（范围从 1900 kbps 到 400 kbps）和 AAC 5.1 音频。  
  
 [H264 多比特率 16x9 SD](media-services-mes-preset-H264-Multiple-Bitrate-16x9-SD.md) 生成一组 5 GOP 对齐的 MP4 文件（范围从 1900 kbps 到 400 kbps）和立体声 AAC 音频。  
  
 [H264 多比特率 4K Audio 5.1](media-services-mes-preset-H264-Multiple-Bitrate-4K-Audio-5.1.md) 生成一组 12 GOP 对齐的 MP4 文件（范围从 20000 kbps 到 1000 kbps）和 AAC 5.1 音频。  
  
 [H264 多比特率 4K](media-services-mes-preset-H264-Multiple-Bitrate-4K.md) 生成一组 12 GOP 对齐的 MP4 文件（范围从 20000 kbps 到 1000 kbps）和立体声 AAC 音频。  
  
 [H264 多比特率 4x3 (iOS)](media-services-mes-preset-H264-Multiple-Bitrate-4x3-for-iOS.md) 生成一组 8 GOP 对齐的 MP4 文件（范围从 8500 kbps 到 200 kbps）和立体声 AAC 音频。  
  
 [H264 多比特率 4x3 SD Audio 5.1](media-services-mes-preset-H264-Multiple-Bitrate-4x3-SD-Audio-5.1.md) 生成一组 5 GOP 对齐的 MP4 文件（范围从 1600 kbps 到 400 kbps）和 AAC 5.1 音频。  
  
 [H264 多比特率 4x3 SD](media-services-mes-preset-H264-Multiple-Bitrate-4x3-SD.md) 生成一组 5 GOP 对齐的 MP4 文件（范围从 1600 kbps 到 400 kbps）和立体声 AAC 音频。  
  
 [H264 多比特率 720p Audio 5.1](media-services-mes-preset-H264-Multiple-Bitrate-720p-Audio-5.1.md) 生成一组 6 GOP 对齐的 MP4 文件（范围从 3400 kbps 到 400 kbps）和 AAC 5.1 音频。  
  
 [H264 多比特率 720p](media-services-mes-preset-H264-Multiple-Bitrate-720p.md)生成一组 6 GOP 对齐的 MP4 文件（范围从 3400 kbps 到 400 kbps）和立体声 AAC 音频。  
  
 [H264 单比特率 1080p Audio 5.1](media-services-mes-preset-H264-Single-Bitrate-1080p-Audio-5.1.md) 生成比特率为 6750 kbps 的单个 MP4 文件和 AAC 5.1 音频。  
  
 [H264 单比特率 1080p](media-services-mes-preset-H264-Single-Bitrate-1080p.md) 生成比特率为 6750 kbps 的单个 MP4 文件和立体声 AAC 音频。  
  
 [H264 单比特率 4K Audio 5.1](media-services-mes-preset-H264-Single-Bitrate-4K-Audio-5.1.md) 生成比特率为 18000 kbps 的单个 MP4 文件和 AAC 5.1 音频。  
  
 [H264 单比特率 4K](media-services-mes-preset-H264-Single-Bitrate-4K.md) 生成比特率为 18000 kbps 的单个 MP4 文件和立体声 AAC 音频。  
  
 [H264 单比特率 4x3 SD Audio 5.1](media-services-mes-preset-H264-Single-Bitrate-4x3-SD-Audio-5.1.md) 生成比特率为 1800 kbps 的单个 MP4 文件和 AAC 5.1 音频。  
  
 [H264 单比特率 4x3 SD](media-services-mes-preset-H264-Single-Bitrate-4x3-SD.md) 生成比特率为 1800 kbps 的单个 MP4 文件和立体声 AAC 音频。  
  
 [H264 单比特率 16x9 SD Audio 5.1](media-services-mes-preset-H264-Single-Bitrate-16x9-SD-Audio-5.1.md) 生成比特率为 2200 kbps 的单个 MP4 文件和 AAC 5.1 音频。  
  
 [H264 单比特率 16x9 SD](media-services-mes-preset-H264-Single-Bitrate-16x9-SD.md) 生成比特率为 2200 kbps 的单个 MP4 文件和立体声 AAC 音频。  
  
 [H264 单比特率 720p Audio 5.1](media-services-mes-preset-H264-Single-Bitrate-720p-Audio-5.1.md) 生成比特率为 4500 kbps 的单个 MP4 文件和 AAC 5.1 音频。  
  
 [H264 单比特率 720p (Android)](media-services-mes-preset-H264-Single-Bitrate-720p-for-Android.md) 预设生成比特率为 2000 kbps 的单个 MP4 文件和立体声 AAC。  
  
 [H264 单比特率 720p](media-services-mes-preset-H264-Single-Bitrate-720p.md) 生成比特率为 4500 kbps 的单个 MP4 文件和立体声 AAC 音频。  
  
 [H264 单比特率高品质 SD (Android)](media-services-mes-preset-H264-Single-Bitrate-High-Quality-SD-for-Android.md) 生成比特率为 500 kbps 的单个 MP4 文件和立体声 AAC 音频。  
  
 [H264 单比特率低质量 SD (Android)](media-services-mes-preset-H264-Single-Bitrate-Low-Quality-SD-for-Android.md) 生成比特率为 56 kbps 的单个 MP4 文件和立体声 AAC 音频。  
  
 有关媒体服务编码器的详细信息，请参阅[使用 Azure 媒体服务按需编码](https://azure.microsoft.com/documentation/articles/media-services-encode-asset/)。
