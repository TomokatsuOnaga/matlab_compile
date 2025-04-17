# MATLAB をコンパイルするデモコード

このリポジトリは MATLAB のコンパイルを試すためのものです。以下のリンクを参考にしています:  
[MATLAB Compiler ドキュメント](https://jp.mathworks.com/help/compiler/create-standalone-app-from-matlab-function.html)

## コンパイル方法

以下のコマンドを MATLAB 内で実行してください:

```matlab
appFile = "magicsquare.m";
buildResults = compiler.build.standaloneApplication(appFile);
```

## 実行方法

各 OS に応じて以下のコマンドを使用してください:

- **Windows**  
    ```cmd
    !magicsquare 4
    ```

- **Linux**  
    ```bash
    !./magicsquare 4
    ```

- **macOS**  
    ```matlab
    system(['./run_magicsquare.sh ', matlabroot, ' 4']);
    ```