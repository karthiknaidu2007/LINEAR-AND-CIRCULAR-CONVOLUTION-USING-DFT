# EXPT 1: LINEAR-AND-CIRCULAR-CONVOLUTION-USING-DFT
## AIM
To perform and verify linear and circular convolution operation of two given sequences
using SCILAB.
## APPARATUS REQUIRED
PC installed with SCILAB
## PROGRAM:
### LINEAR CONVOLUTION
<br>

```
clc;
clear;

x = [1 1 1 1];
h = [1 2 3 4];

m = length(x);
n = length(h);

a = 0:m-1;
b = 0:n-1;

subplot(3,1,1);
plot2d3(a, x);
xlabel('Time');
ylabel('Amplitude');
title('Graphical Representation of Input Signal x');

subplot(3,1,2);
plot2d3(b, h);
xlabel('Time');
ylabel('Amplitude');
title('Graphical Representation of Impulse Signal h');

y = zeros(1, m+n-1);

for i = 1:m+n-1
    conv_sum = 0;
    for j = 1:m
        if ((i-j+1) >= 1) & ((i-j+1) <= n) then
            conv_sum = conv_sum + x(j) * h(i-j+1);
        end
    end
    y(i) = conv_sum;
end

disp(y, 'Convolution Sum using Direct Formula Method =');

subplot(3,1,3);
plot2d3(0:m+n-2, y);
xlabel('Time');
ylabel('Amplitude');
title('Graphical Representation of Output Signal y');

```
<br>

### CALCULATIONS:
<br>

![WhatsApp Image 2026-03-09 at 7 00 23 PM](https://github.com/user-attachments/assets/6c736881-f1ba-46c1-b89e-7c84814268d4)

![WhatsApp Image 2026-03-09 at 7 00 49 PM](https://github.com/user-attachments/assets/aeeae18a-8ef5-4009-9c37-6418ddf722c4)

<br>
<br>

### SAMPLE OUTPUT:
<br>
<br>
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/b2e2ac31-2090-43b1-b8b7-b2d6f169a182" />


<br>
<br>

## CIRCULAR CONVOLUTION:
<br>
<br>

```
clc;
clear;

x = [1 1 1 1];
n1 = 0:length(x)-1;

subplot(3,1,1);
plot2d3(n1, x);
xlabel('time');
ylabel('amplitude');
title('input sequence');

h = [1 2 3];
n2 = 0:length(h)-1;

subplot(3,1,2);
plot2d3(n2, h);
xlabel('time');
ylabel('amplitude');
title('impulse sequence');

N1 = length(x);
N2 = length(h);
N = max(N1, N2);
N3 = N1 - N2;

if N3 > 0 then
    h = [h zeros(1, N3)];
else
    x = [x zeros(1, abs(N3))];
end

y = zeros(1, N);

for n = 1:N
    for i = 1:N
        j = n - i + 1;
        if j <= 0 then
            j = N + j;
        end
        y(n) = y(n) + x(i) * h(j);
    end
end

disp(y);

n3 = 0:N-1;
subplot(3,1,3);
plot2d3(n3, y);
xlabel('time');
ylabel('amplitude');
title('circular convolution');

```

### CALCULATIONS:

<br>
<br>

![WhatsApp Image 2026-03-09 at 7 01 14 PM](https://github.com/user-attachments/assets/ee2473e1-94fd-404b-b5d2-06c8367f64b3)


<br>

### SAMPLE OUTPUT:
<br>

<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/0b51e070-ca2d-40b7-9702-3b567f6c062a" />

<br>
<br>


## RESULT:
Thus, the linear convolution and circular convolution of the two given sequences were performed and its result was verified.
