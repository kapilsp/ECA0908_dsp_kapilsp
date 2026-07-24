clc;
clear;
close all;

% EX NO: 1
% Butterworth IIR Low-Pass Filter Design

% Filter Specifications
Fs = 8000;      % Sampling Frequency (Hz)
Fp = 1000;      % Passband Frequency (Hz)
Fst = 3000;     % Stopband Frequency (Hz)
Rp = 1;         % Passband Ripple (dB)
Rs = 20;        % Stopband Attenuation (dB)

% Calculate Filter Order and Cutoff Frequency
[N, Wn] = buttord(Fp/(Fs/2), Fst/(Fs/2), Rp, Rs);

% Design Butterworth Low-Pass Filter
[b, a] = butter(N, Wn, 'low');

% Display Filter Parameters
fprintf('Minimum Filter Order (N) = %d\n', N);
fprintf('Cutoff Frequency (Wn) = %.4f\n', Wn);

% Magnitude and Phase Response
figure;
freqz(b, a);
title('Magnitude and Phase Response');

% Impulse Response
figure;
impz(b, a);
title('Impulse Response');

% Step Response
figure;
step = filter(b, a, ones(1,50));
stem(step, 'filled');
grid on;
title('Step Response');
xlabel('Samples');
ylabel('Amplitude');

% Pole-Zero Plot
figure;
zplane(b, a);
title('Pole-Zero Plot');

% Test Signal
t = 0:1/Fs:0.01;
x = sin(2*pi*500*t) + sin(2*pi*3500*t);

% Filtered Output
y = filter(b, a, x);

% Plot Input and Output Signals
figure;
subplot(2,1,1);
plot(t, x);
grid on;
title('Input Signal');
xlabel('Time (s)');
ylabel('Amplitude');

subplot(2,1,2);
plot(t, y);
grid on;
title('Filtered Output Signal');
xlabel('Time (s)');
ylabel('Amplitude');
