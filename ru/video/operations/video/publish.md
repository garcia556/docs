---
title: "Как опубликовать видео в {{ video-full-name }}"
description: "Следуя данной инструкции, вы сможете опубликовать и проверить доступность видео, загруженного в сервис {{ video-full-name }}."
---

# Опубликовать видео

Вы можете опубликовать видео и проверить его доступность.

## Опубликуйте видео {#publish-video}

{% list tabs group=instructions %}

- Интерфейс {{ video-name }} {#console}

  1. [Загрузите](upload.md) видео.
  1. Дождитесь, пока видео полностью загрузится, обработается и перейдет в статус `Ready`.
  1. Включите опцию **{{ ui-key.yacloud_video.videos.label_allow-access }}**.

      Видео перейдет в статус `Published`.

- API {#api}

  Воспользуйтесь вызовом gRPC API [VideoService/Create](../../api-ref/grpc/video_service.md#Create).

{% endlist %}

## Проверьте доступность видео {#test}

{% list tabs group=instructions %}

- Интерфейс {{ video-name }} {#console}

  1. Откройте [главную страницу]({{ link-video-main }}) {{ video-name }}.
  1. Выберите канал.
  1. На вкладке ![image](../../../_assets/console-icons/circle-play.svg) **{{ ui-key.yacloud_video.videos.title_videos }}** выберите нужное видео.
  1. На открывшейся странице с параметрами видео в блоке **{{ ui-key.yacloud_video.videos.title_past-code }}** выберите вкладку `link`.
  1. Нажмите кнопку ![copy](../../../_assets/console-icons/copy.svg) **{{ ui-key.yacloud_video.streams.action_copy-code }}**.
  1. Откройте новую страницу браузера и вставьте в адресной строке полученную ссылку.
  1. Нажмите кнопку воспроизведения.

- API {#api}

  Воспользуйтесь вызовом gRPC API [VideoService/GetPlayerURL](../../api-ref/grpc/video_service.md#GetPlayerURL).

{% endlist %}

#### См. также {#see-also}

[{#T}](get-link.md)
[{#T}](download.md)