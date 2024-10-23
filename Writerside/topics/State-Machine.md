# State Machine

State Machine with 4 states (A, B, C, D). Reset input will return to state A and will only go in a single direction
(A -> B -> C -> D -> A). 

###### Entity
```
entity StateMachine is
    port (CLK : in std_logic;
          Input, Reset : in std_logic;
          T : out std_logic);
end entity;
```

###### Architecture
```
architecture StateMachine_Arch of StateMachine is
    type State_Type is (A, B, C, D); 
    --While technically this works it's best to change the state names

    signal current_state, next_state : State_Type;

    begin
    Next_State_Logic : process (current_state, Input)
        begin
        end process;
    State_Memory : process (CLK, Reset)
        begin
        end process;
    Output_Logic : process (current_state)
        begin
        end process;
end architecture
```

###### Next State Logic
```
Next_State_Logic : process (current_state, Input)
    begin
    case (current_state) is
        when A => next_state <= B;
        when B => if (Input = '0') then
                    next_state <= C;
                  else
                    next_state <= A;
                  end if;
        when C => next_state <= D;
        when D => next_state <= A;
        when others => next_state <= A;
    end case;
end process;
```

###### State Memory
Functionally similar to the Register <a href="Registers.md">Register Process</a>, but the size of the vector
does not need to be defined.

```
State_Memory : process (CLK, Reset)
    begin
    if (Reset = '0') then
        current_state <= A;
    elsif (CLK'event and CLK='0') then
        current_state <= next_state;
    end if;
end process;
```

###### Output Logic
```
Output_Logic : process (current_state)
    begin
    case (current_state) is
        when A => T <= '0';
        when B => T <= '1';
        when C => T <= '1';
        when D => T <= '0';
        when others => T <= '0';
    end case;
end process;
```