# Counter

20-bit counter. This assumes the ```signal Count20 : unsigned (19 downto 0);``` is defined in the architecture,
and that there is a clock signal to allow the counter to increment.

###### Counter Process
```
Counter20_Process : process (clk)
    begin
        if (Count20 = 1000000) then 
            Count20 <= to_unsigned(0, 20);
        elsif (rising_edge(clk)) then
            Count20 <= Count20 + 1;
        end if;
        
        if (Count20 < 500000) then
            ClkShrt <= '1';
        else 
            ClkShrt <= '0';
        end if;
    end process;
```