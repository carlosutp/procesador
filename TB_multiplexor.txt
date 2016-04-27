--------------------------------------------------------------------------------
-- Company: 
-- Engineer:
--
-- Create Date:   16:10:49 04/27/2016
-- Design Name:   
-- Module Name:   C:/Users/carlos/Desktop/procesador/prosesador1/tb_mpx.vhd
-- Project Name:  prosesador1
-- Target Device:  
-- Tool versions:  
-- Description:   
-- 
-- VHDL Test Bench Created by ISE for module: mpx
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
 
ENTITY tb_mpx IS
END tb_mpx;
 
ARCHITECTURE behavior OF tb_mpx IS 
 
    -- Component Declaration for the Unit Under Test (UUT)
 
    COMPONENT mpx
    PORT(
         mpx_crs2 : IN  std_logic_vector(31 downto 0);
         mpx_i : IN  std_logic;
         mpx_seu : IN  std_logic_vector(31 downto 0);
         mpx_out : OUT  std_logic_vector(31 downto 0)
        );
    END COMPONENT;
    

   --Inputs
   signal mpx_crs2 : std_logic_vector(31 downto 0) := (others => '0');
   signal mpx_i : std_logic := '0';
   signal mpx_seu : std_logic_vector(31 downto 0) := (others => '0');

 	--Outputs
   signal mpx_out : std_logic_vector(31 downto 0);
   -- No clocks detected in port list. Replace <clock> below with 
   -- appropriate port name 
 
   --constant <clock>_period : time := 10 ns;
 
BEGIN
 
	-- Instantiate the Unit Under Test (UUT)
   uut: mpx PORT MAP (
          mpx_crs2 => mpx_crs2,
          mpx_i => mpx_i,
          mpx_seu => mpx_seu,
          mpx_out => mpx_out
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
      mpx_crs2 <= X"00000003";
		mpx_seu<= X"00000002";
		mpx_i<= '1';
		
		 wait for 100 ns;
		 
		 mpx_crs2 <= X"00000003";
		mpx_seu<= X"00000002";
      mpx_i<= '0';
		wait for 100 ns; 

      wait;
   end process;

END;
