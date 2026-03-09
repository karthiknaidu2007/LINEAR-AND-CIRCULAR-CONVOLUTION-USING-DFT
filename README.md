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

![WhatsApp Image 2026-03-09 at 7 00 23 PM](https://github.com/user-attachments/assets/5ed1273e-6a13-4aa4-a791-4101fe722c14)


![WhatsApp Image 2026-03-09 at 7 00 49 PM](https://github.com/user-attachments/assets/5f64eec5-0785-4eaa-a1aa-e5021ff02ede)


<br>
### SAMPLE OUTPUT:
<br>

<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/1051bf33-c22f-4f5a-b47b-4d4d9539432f" />

<br>

## CIRCULAR CONVOLUTION
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
<br>
### CALCULATIONS:
<br>

![WhatsApp Image 2026-03-09 at 7 01 14 PM](https://github.com/user-attachments/assets/85e18795-fc00-453f-a131-dd05128a17e1)

<br>
### SAMPLE OUTPUT:
<br>

<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/4ba2fb4a-66f2-461a-bcb4-9f35173d4207" />

<br>

## RESULT:
Thus, the linear convolution and circular convolution of the two given sequences were performed and its result was verified.
