# Atividade de desenvolvimento de aprendizado

## Objetivo
Desenvolver uma ideia de VR e AR para demonstração de aprendizagem do módulo eletivo de Experiências Imersivas.

Logo abaixo, está a atividade de desenvolvimento de aprendizado, que consiste em criar um projeto de realidade aumentada utilizando a biblioteca A-Frame.

Resumidamente, o código importa a biblioteca A-Frame e AR.js, cria um cenário de realidade aumentada, adiciona um recurso de imagem e uma entidade de câmera. Com isso é possível visualizar um cubo em realidade aumentada.

A base do código é a seguinte:

```javascript
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Primeiro AR</title>
    <!-- A-Frame itself -->
    <script src="https://aframe.io/releases/1.3.0/aframe.min.js"></script>

    <!-- Pure three.js code that the A-Frame components use for location-based AR -->
    <script type='text/javascript' src='https://raw.githack.com/AR-js-org/AR.js/3.4.5/three.js/build/ar-threex-location-only.js'></script>

    <!-- AR.js A-Frame components -->
    <script type='text/javascript' src='https://raw.githack.com/AR-js-org/AR.js/3.4.5/aframe/build/aframe-ar.js'></script>
</head>
</html>
```

A partir desta base, foram feitas 4 implementações de realidade aumentada, que são:

1. **Exercício 1**: Adicionar um cubo em realidade aumentada.

```javascript
<!-- Preenche o conteúdo da página sem a necessidade de barra de rolagem -->
<body style="margin: 0px; overflow: hidden;">
    
    <!-- Cria um cenário de realidade aumentada -->
    <a-scene vr-mode-ui="enabled: false" arjs="debugUIEnabled: false">
        
        <!-- Adiciona um recurso de imagem -->
        <a-marker preset="hiro">
            <a-box color="#ff0e0e0e"></a-box>
        </a-marker>
        
        <!-- Adiciona uma entidade de câmera -->
        <a-entity camera=""></a-entity>
    
    </a-scene>
</body>
```

2. **Exercício 2**: Adicionar uma imagem em realidade aumentada.

```javascript
<!-- Preenche o conteúdo da página sem a necessidade de barra de rolagem -->
<body style="margin: 0px; overflow: hidden;">

    <!-- Cria um cenário de realidade aumentada -->
    <a-scene vr-mode-ui="enabled: false" arjs="debugUIEnabled: false">

        <!-- Adiciona um asset de imagem -->
        <a-assets>
            <img id="sete" src="./assets/004.png"/>
        </a-assets>

        <!-- Adiciona um marcador para a imagem -->
        <a-marker preset="hiro">
            <a-image width="1" height="1" rotation="-90 0 0" position="0 0 0" src="#sete"></a-image>
        </a-marker>

        <!-- Adiciona uma entidade de câmera -->
        <a-entity camera=""></a-entity>
    </a-scene>
</body>
```

3. **Exercício 3**: Adicionar um vídeo e som em realidade aumentada.

```javascript
<!-- Preenche o conteúdo da página sem a necessidade de barra de rolagem -->
<body style="margin: 0px; overflow: hidden;">

    <!-- Cria um cenário de realidade aumentada -->
    <a-scene vr-mode-ui="enabled: false" arjs="debugUIEnabled: false">

        <!-- Adiciona um asset de imagem, vídeo e som -->
        <a-assets>
            <audio id="som" preload="auto" src="./assets/mixkit-small-group-cheer-and-applause-518.wav"></audio>
            <video id="video" src="./assets/robos.mp4" autoplay loop></video>
            <img id="imagem" src="./assets/004.png"/>
        </a-assets>

        <!-- Adiciona um marcador para o vídeo e o som -->
        <a-marker preset="hiro">
            <a-video src="#video" width="2" height="2" rotation="-90 0 0" position="0 0 0"></a-video>
            <a-entity sound="src: #som; autoplay: true; loop: true"></a-entity>
        </a-marker>

        <!-- Adiciona uma entidade de câmera -->
        <a-entity camera=""></a-entity>
    </a-scene>
</body>
```

4. **Exercício 4**: Adicionar um modelo 3D em realidade aumentada.

```javascript
<!-- Preenche o conteúdo da página sem a necessidade de barra de rolagem -->
<body style="margin: 0px; overflow: hidden;">
    
    <!-- Cria um cenário de realidade aumentada -->
    <a-scene vr-mode-ui="enabled: false" arjs="debugUIEnabled: false">

        <!-- Adiciona um recurso de objeto com extensão ".gltf" -->
        <a-assets>
            <!--Estadio 3D-->
            <a-asset-item id="estadio" src="./assets/estadio.gltf"></a-asset-item>
        </a-assets>

        <!-- Adiciona um marcador para o objeto 3D -->
        <a-marker preset="hiro">
            <a-entity gltf-model="#estadio" scale="0.03 0.03 0.03" position="0 0 0"></a-entity>
        </a-marker>

        <!-- Adiciona uma entidade de câmera -->
        <a-entity camera=""></a-entity>
    </a-scene>
</body>
```