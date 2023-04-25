pipeline {
    agent none
    stage("AFL") {
        agent {
            docker {
                image "aflplusplus/aflplusplus"
            }
        }
        stages {
            stage("Build") {
                environment {
                    AFL_USE_ASAN = 1
                }
                steps {
                    sh """
                        cmake -B build/Fuzzing . \
                            -DCMAKE_CXX_COMPILER=afl-clang-lto++ \
                            -DCMAKE_LINKER=afl-clang-lto \
                            -DCMAKE_AR=llvm-ar-14 \
                            -DCMAKE_CXX_COMPILER_RANLIB=llvm-ranlib-14
                    """
                    sh "cmake --build build/Fuzzing --target bmp2png -j \$(nproc)"
                }
            }
        }
    }
}
