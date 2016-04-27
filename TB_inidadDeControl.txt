--------------------------------------------------------------------------------
-- Company: 
-- Engineer:
--
-- Create Date:   19:38:04 04/26/2016
-- Design Name:   
-- Module Name:   C:/Users/carlos/Desktop/procesador/prosesador1/tb_cu.vhd
-- Project Name:  prosesador1
-- Target Device:  
-- Tool versions:  
-- Description:   
-- 
-- VHDL Test Bench Created by ISE for module: cu
-- 
-- Dependencies:
-- 
-- Revision:
-- Revision 0.01 - File Created
-- Additional Comments:
--
-- Notes: 
-- This testbench has been automatically generated using types std_logic and
-- std_logic_vector for the ports of the unit under test.  Xilinx recommends
-- that these types always be used for the top-level I/O of a design in order
-- to guarantee that the testbench will bind correctly to the post-implementation 
-- simulation model.
--------------------------------------------------------------------------------
LIBRARY ieee;
USE ieee.std_logic_1164.ALL;
 
-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--USE ieee.numeric_std.ALL;
 
ENTITY tb_cu IS
END tb_cu;
 
ARCHITECTURE behavior OF tb_cu IS 
 
    -- Component Declaration for the Unit Under Test (UUT)
 
    COMPONENT cu
    PORT(
         cu_op : IN  std_logic_vector(1 downto 0);
         cu_op3 : IN  std_logic_vector(5 downto 0);
         cu_aluop : OUT  std_logic_vector(5 downto 0)
        );
    END COMPONENT;
    

   --Inputs
   signal cu_op : std_logic_vector(1 downto 0) := (others => '0');
   signal cu_op3 : std_logic_vector(5 downto 0) := (others => '0');

 	--Outputs
   signal cu_aluop : std_logic_vector(5 downto 0);
   -- No clocks detected in port list. Replace <clock> below with 
   -- appropriate port name 
 
   --constant <clock>_period : time := 10 ns;
 
BEGIN
 
	-- Instantiate the Unit Under Test (UUT)
   uut: cu PORT MAP (
          cu_op => cu_op,
          cu_op3 => cu_op3,
          cu_aluop => cu_aluop
        );

   -- Clock process definitions
   --<clock>_process :process
   --begin
	--	<clock> <= '0';
	--	wait for <clock>_period/2;
	--	<clock> <= '1';
	--	wait for <clock>_period/2;
   --end process;
 

   -- Stimulus process
   stim_proc: process
   begin		
      cu_op <= "10";
		
		cu_op3 <= "000000" ;
			
      wait for 100 ns;
		cu_op <= "10";
		
		cu_op3 <= "000001" ;
				
      wait for 100 ns;
		cu_op <= "10";
		
		cu_op3 <= "000100" ;
				
      wait;	 

      wait;
   end process;

END;
