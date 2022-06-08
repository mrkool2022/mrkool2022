Ta = 25;
Tini = 30;
T1 = 30;
T2 = 30;
T3 = 30;
T4 = 30;
T5 = 30;
h = 50208;
k = 1.9*3600;
roh = 2400;
Cp = 800;
L = 2;
dx = L/4;
mmax = 5;
tmax = 5;
T = zeros(mmax,tmax);
T(:,1) = 30;
for i = 2:5
    dt = (i-1)*dt;
    T(1,i) = T(1,i)+((2*h*dt*(Ta-T1))/(roh*Cp*dx)+(2*k*dt*(T2-T1))/(roh*Cp*(dx^2))+((2*dt)/roh*Cp)*(-(1*dt)^2+20*(dt)));
    T(2,i) = T(1,i)+((T1*k*dt)/(roh*Cp*(dx^2))+T2*(1-2*((k*dt)/(roh*Cp*(dx^2))))+(T3*k*dt)/(roh*Cp*(dx^2))+(dt/(roh*Cp))*(-(2*dt)^2+20*(2*dt)));
    T(3,i) = T(1,i)+((T2*k*dt)/(roh*Cp*(dx^2))+T3*(1-2*((k*dt)/(roh*Cp*(dx^2))))+(T4*k*dt)/(roh*Cp*(dx^2))+(dt/(roh*Cp))*(-(3*dt)^2+20*(3*dt)));
    T(4,i) = T(1,i)+((T3*k*dt)/(roh*Cp*(dx^2))+T4*(1-2*((k*dt)/(roh*Cp*(dx^2))))+(T5*k*dt)/(roh*Cp*(dx^2))+(dt/(roh*Cp))*(-(4*dt)^2+20*(4*dt)));
    T(5,i) = T(1,i)+((2*h*dt*(Ta-T5))/(roh*Cp*dx)+(2*k*dt*(T4-T5))/(roh*Cp*(dx^2))+((2*dt)/roh*Cp)*(-(5*dt)^2+(20*5*dt)));
end
disp(T)
figure
plot(T(1,:))
