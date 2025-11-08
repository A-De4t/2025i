# 2025i
ak
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// 多个喀什专属号段，可以自行添加或修改
const char* prefixes[] = {
    "155", "166", "188", "139", "147"
};
#define PREFIX_COUNT (sizeof(prefixes) / sizeof(prefixes[0]))
#define PHONE_COUNT 1000 // 需要生成的手机号数量

// 随机生成8位数字字符串
void generate_random_8_digits(char* buffer) {
    for (int i = 0; i < 8; ++i) {
        buffer[i] = '0' + rand() % 10;
    }
    buffer[8] = '\0';
}

int main() {
    srand((unsigned int)time(NULL));

    for (int i = 0; i < PHONE_COUNT; ++i) {
        char last8[9];
        generate_random_8_digits(last8);
        // 随机选取一个号段
        const char* prefix = prefixes[rand() % PREFIX_COUNT];
        printf("%s%s\n", prefix, last8);
    }

    return 0;
}
