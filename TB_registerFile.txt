--------------------------------------------------------------------------------
-- Company: 
-- Engineer:
--
-- Create Date:   18:38:08 04/26/2016
-- Design Name:   
-- Module Name:   C:/Users/carlos/Desktop/procesador/prosesador1/tb_rf.vhd
-- Project Name:  prosesador1
-- Target Device:  
-- Tool versions:  
-- Description:   
-- 
-- VHDL Test Bench Created by ISE for module: rf
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
 
ENTITY tb_rf IS
END tb_rf;
 
ARCHITECTURE behavior OF tb_rf IS 
 
    -- Component Declaration for the Unit Under Test (UUT)
 
    COMPONENT rf
    PORT(
         rs1 : IN  std_logic_vector(4 downto 0);
         rs2 : IN  std_logic_vector(4 downto 0);
         rd : IN  std_logic_vector(4 downto 0);
         in1 : IN  std_logic_vector(31 downto 0);
         crs1 : OUT  std_logic_vector(31 downto 0);
         crs2 : OUT  std_logic_vector(31 downto 0);
         reset : IN  std_logic
        );
    END COMPONENT;
    

   --Inputs
   signal rs1 : std_logic_vector(4 downto 0) := (others => '0');
   signal rs2 : std_logic_vector(4 downto 0) := (others => '0');
   signal rd : std_logic_vector(4 downto 0) := (others => '0');
   signal in1 : std_logic_vector(31 downto 0) := (others => '0');
   signal reset : std_logic := '0';

 	--Outputs
   signal crs1 : std_logic_vector(31 downto 0);
   signal crs2 : std_logic_vector(31 downto 0);
   -- No clocks detected in port list. Replace <clock> below with 
   -- appropriate port name 
 
  -- constant <clock>_period : time := 10 ns;
 
BEGIN
 
	-- Instantiate the Unit Under Test (UUT)
   uut: rf PORT MAP (
          rs1 => rs1,
          rs2 => rs2,
          rd => rd,
          in1 => in1,
          crs1 => crs1,
          crs2 => crs2,
          reset => reset
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
     rs1<="00001" ;
   rs2 <="00010";
   rd <="00001";
   reset<='1';
   

      wait for 100 ns;	


	rs1<="00001" ;
   rs2 <="00010";
   rd <= "00001";
   reset<='0';
   

      wait for 100 ns;	
     
	 rs1<="00001" ;
   rs2 <="00010";
   rd <= "00011";
   reset<='0';
   

      wait for 100 ns;	
 rs1<="00011" ;
   rs2 <="00110";
   rd <= "00010";
   reset<='0';
  

      wait for 100 ns;	
      wait;
   end process;

END;
