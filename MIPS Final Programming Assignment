#################################################################################
#	PURPOSE:	This program lets the user enter values for, and subsequently compute, a polynomial.
#
#	INPUTS:		User Input after being prompted for degree of polynomial				- stored in nDegree
#			User Input after Error message is displayed
#			User Input after being prompted for coefficients					- stored in aCoef
#			User Input after being prompted for variable x						- stored in xValue
#			User Input after being asked whether to evaluate the polynomial for a new x value
#			User Input after being asked whether to evaluate a new polynomial
#
#	OUTPUTS:	resultPrompt is a string that is displayed on screen when the polynomial has been computed
#			polyResult is an integer that holds the result of the polynomial
#			nErrorPrompt is a string that is displayed on screen when the user inputs an invalid value of n
#			
#################################################################################

		.data			
cycleCount:	.word	-1
nDegree:	.word	0
xValue:		.word	0
polyResult:	.word	0
aCoef:		.asciiz	"..........."     
degreePrompt:	.asciiz "Enter your degree of n. Must be from 0 - 10. \n"
coeffPrompt:	.asciiz	"Enter your signed coefficents from coefficient 0 - coefficient n. (Make sure to press enter after each coefficient) \n"
xPrompt:	.asciiz "Please enter the value of x for your polynomial \n"
resultPrompt:	.asciiz	"The result of your polynomial is "
newXPrompt:	.asciiz "\n Would you like to enter a new value of x to compute? Enter 0 for no or any other integer for yes. \n"
newPolyPrompt:	.asciiz "Would you like to evaluate a different polynomial? Enter 0 for no or any other integer for yes \n"
nErrorPrompt:	.asciiz	"Invalid degree of n. \n"

		.text
main:
	lw	$s0, nDegree			#
	la	$s1, aCoef			#
	lw	$s2, xValue			#
	lw	$s3, cycleCount			#
	lw	$s4, polyResult			#
getDegree:					#
	li	$v0, 4				# "Enter your polynomial degree" prompt
	la	$a0, degreePrompt		# -
	syscall					# -
	li	$v0, 5				# nDegree = Keyboard.nextInt();
	syscall					# - 
	move	$s0, $v0			# - 
	blt 	$s0, 0, nError			# if (nDegree < 0)
	bgt	$s0, 10, nError			# if (nDegree > 10)
	li 	$v0, 4				# "Enter a coefficient" prompt
	la	$a0, coeffPrompt		# - 
	syscall					# - 
getCoefficients:				#
	addi	$sp, $sp, -4			# Make room on the stack as a placeholder for coefficients
	li	$v0, 5				# Coefficient_n = Keyboard.nextInt();
	syscall					# -
	sw	$v0, 0($sp)			# -
	add  	$s3, $s3, 1			# cycleCount += 1;
	blt	$s3, $s0, getCoefficients	# if (cycleCount < nDegree)
coefficientTransfer:				#
	beq	$s0, 0, degreeZeroCoefficients	# if(nDegree == 0)
	beq	$s0, 1, degreeOneCoefficients	# if(nDegree == 1)
	beq	$s0, 2, degreeTwoCoefficients	# if(nDegree == 2)
	beq	$s0, 3, degreeThreeCoefficients	# if(nDegree == 3)
	beq	$s0, 4, degreeFourCoefficients	# if(nDegree == 4)
	beq	$s0, 5, degreeFiveCoefficients	# if(nDegree == 5)
	beq	$s0, 6, degreeSixCoefficients	# if(nDegree == 6)
	beq	$s0, 7, degreeSevenCoefficients	# if(nDegree == 7)
	beq	$s0, 8, degreeEightCoefficients	# if(nDegree == 8)
	beq	$s0, 9, degreeNineCoefficients	# if(nDegree == 9)
	beq	$s0, 10, degreeTenCoefficients	# if(nDegree == 10)
degreeZeroCoefficients:				# 
	lw	$t1, 0($sp)			# aCoef[0] = coefficient_0;
	sw	$t1, 0($s1)			# -
	addi	$sp, $sp, 4			#
	j	getX				#
degreeOneCoefficients:				#
	lw	$t1, 4($sp)			# aCoef[0] = coefficient_0;
	lw	$t2, 0($sp)			# aCoef[1] = coefficient_1;
	sw	$t1, 0($s1)			# -
	sw	$t2, 4($s1)			# -
	addi	$sp, $sp, 8			#
	j	getX				#
degreeTwoCoefficients:				#
	lw	$t1, 8($sp)			# aCoef[0] = coefficient_0;
	lw	$t2, 4($sp)			# aCoef[1] = coefficient_1;
	lw	$t3, 0($sp)			# aCoef[2] = coefficient_2;
	sw	$t1, 0($s1)			# -
	sw	$t2, 4($s1)			# -
	sw	$t3, 8($s1)			# -
	addi	$sp, $sp, 12			#
	j	getX				#
degreeThreeCoefficients:			#
	lw	$t1, 12($sp)			# aCoef[0] = coefficient_0;
	lw	$t2, 8($sp)			# aCoef[1] = coefficient_1;
	lw	$t3, 4($sp)			# aCoef[2] = coefficient_2;
	lw	$t4, 0($sp)			# aCoef[3] = coefficient_3;
	sw	$t1, 0($s1)			# -
	sw	$t2, 4($s1)			# -
	sw	$t3, 8($s1)			# -
	sw	$t4, 12($s1)			# -
	addi	$sp, $sp, 16			#
	j	getX				#
degreeFourCoefficients:				#
	lw	$t1, 16($sp)			# aCoef[0] = coefficient_0;
	lw	$t2, 12($sp)			# aCoef[1] = coefficient_1;
	lw	$t3, 8($sp)			# aCoef[2] = coefficient_2;
	lw	$t4, 4($sp)			# aCoef[3] = coefficient_3;
	lw	$t5, 0($sp)			# aCoef[4] = coefficient_4;
	sw	$t1, 0($s1)			# -
	sw	$t2, 4($s1)			# -
	sw	$t3, 8($s1)			# -
	sw	$t4, 12($s1)			# -
	sw	$t5, 16($s1)			# -
	addi	$sp, $sp, 20			#
	j	getX				#
degreeFiveCoefficients:				#
	lw	$t1, 20($sp)			# aCoef[0] = coefficient_0;
	lw	$t2, 16($sp)			# aCoef[1] = coefficient_1;
	lw	$t3, 12($sp)			# aCoef[2] = coefficient_2;
	lw	$t4, 8($sp)			# aCoef[3] = coefficient_3;
	lw	$t5, 4($sp)			# aCoef[4] = coefficient_4;
	lw	$t6, 0($sp)			# aCoef[5] = coefficient_5;
	sw	$t1, 0($s1)			# -
	sw	$t2, 4($s1)			# -
	sw	$t3, 8($s1)			# -
	sw	$t4, 12($s1)			# -
	sw	$t5, 16($s1)			# -
	sw	$t6, 20($s1)			# -
	addi	$sp, $sp, 24			#
	j	getX				#
degreeSixCoefficients:				#
	lw	$t1, 24($sp)			# aCoef[0] = coefficient_0;
	lw	$t2, 20($sp)			# aCoef[1] = coefficient_1;
	lw	$t3, 16($sp)			# aCoef[2] = coefficient_2;
	lw	$t4, 12($sp)			# aCoef[3] = coefficient_3;
	lw	$t5, 8($sp)			# aCoef[4] = coefficient_4;
	lw	$t6, 4($sp)			# aCoef[5] = coefficient_5;
	lw	$t7, 0($sp)			# aCoef[6] = coefficient_6;
	sw	$t1, 0($s1)			# -
	sw	$t2, 4($s1)			# -
	sw	$t3, 8($s1)			# -
	sw	$t4, 12($s1)			# -
	sw	$t5, 16($s1)			# -
	sw	$t6, 20($s1)			# -
	sw	$t7, 24($s1)			# -
	addi	$sp, $sp, 28			#
	j	getX				#
degreeSevenCoefficients:			#
	lw	$t1, 28($sp)			# aCoef[0] = coefficient_0;
	lw	$t2, 24($sp)			# aCoef[1] = coefficient_1;
	lw	$t3, 20($sp)			# aCoef[2] = coefficient_2;
	lw	$t4, 16($sp)			# aCoef[3] = coefficient_3;
	lw	$t5, 12($sp)			# aCoef[4] = coefficient_4;
	lw	$t6, 8($sp)			# aCoef[5] = coefficient_5;
	lw	$t7, 4($sp)			# aCoef[6] = coefficient_6;
	lw	$t8, 0($sp)			# aCoef[7] = coefficient_7;
	sw	$t1, 0($s1)			# -
	sw	$t2, 4($s1)			# -
	sw	$t3, 8($s1)			# -
	sw	$t4, 12($s1)			# -
	sw	$t5, 16($s1)			# -
	sw	$t6, 20($s1)			# -
	sw	$t7, 24($s1)			# -
	sw	$t8, 28($s1)			# -
	addi	$sp, $sp, 32			#
	j	getX				#
degreeEightCoefficients:			#
	lw	$t1, 32($sp)			# aCoef[0] = coefficient_0;
	lw	$t2, 28($sp)			# aCoef[1] = coefficient_1;
	lw	$t3, 24($sp)			# aCoef[2] = coefficient_2;
	lw	$t4, 20($sp)			# aCoef[3] = coefficient_3;
	lw	$t5, 16($sp)			# aCoef[4] = coefficient_4;
	lw	$t6, 12($sp)			# aCoef[5] = coefficient_5;
	lw	$t7, 8($sp)			# aCoef[6] = coefficient_6;
	lw	$t8, 4($sp)			# aCoef[7] = coefficient_7;
	lw	$t9, 0($sp)			# aCoef[8] = coefficient_8;
	sw	$t1, 0($s1)			# -
	sw	$t2, 4($s1)			# -
	sw	$t3, 8($s1)			# -
	sw	$t4, 12($s1)			# - 
	sw	$t5, 16($s1)			# -
	sw	$t6, 20($s1)			# -
	sw	$t7, 24($s1)			# -
	sw	$t8, 28($s1)			# -
	sw	$t9, 32($s1)			# -
	addi	$sp, $sp, 36			#
	j	getX				#
degreeNineCoefficients:				#
	lw	$t1, 36($sp)			# aCoef[0] = coefficient_0;
	lw	$t2, 32($sp)			# aCoef[1] = coefficient_1;
	lw	$t3, 28($sp)			# aCoef[2] = coefficient_2;
	lw	$t4, 24($sp)			# aCoef[3] = coefficient_3;
	lw	$t5, 20($sp)			# aCoef[4] = coefficient_4;
	lw	$t6, 16($sp)			# aCoef[5] = coefficient_5;
	lw	$t7, 12($sp)			# aCoef[6] = coefficient_6;
	lw	$t8, 8($sp)			# aCoef[7] = coefficient_7;
	lw	$t9, 4($sp)			# aCoef[8] = coefficient_8;
	lw	$s7, 0($sp)			# aCoef[9] = coefficient_9;
	sw	$t1, 0($s1)			# -
	sw	$t2, 4($s1)			# -
	sw	$t3, 8($s1)			# -
	sw	$t4, 12($s1)			# - 
	sw	$t5, 16($s1)			# - 
	sw	$t6, 20($s1)			# -
	sw	$t7, 24($s1)			# -
	sw	$t8, 28($s1)			# -
	sw	$t9, 32($s1)			# -
	sw	$s7, 36($s1)			# -
	addi	$sp, $sp, 40			#
	j	getX				#
degreeTenCoefficients:				#
	lw	$t1, 40($sp)			# aCoef[0] = coefficient_0;
	lw	$t2, 36($sp)			# aCoef[1] = coefficient_1;
	lw	$t3, 32($sp)			# aCoef[2] = coefficient_2;
	lw	$t4, 28($sp)			# aCoef[3] = coefficient_3;
	lw	$t5, 24($sp)			# aCoef[4] = coefficient_4;
	lw	$t6, 20($sp)			# aCoef[5] = coefficient_5;
	lw	$t7, 16($sp)			# aCoef[6] = coefficient_6;
	lw	$t8, 12($sp)			# aCoef[7] = coefficient_7;
	lw	$t9, 8($sp)			# aCoef[8] = coefficient_8;
	lw	$s7, 4($sp)			# aCoef[9] = coefficient_9;
	lw	$s6, 0($sp)			# aCoef[10] = coefficient_10;
	sw	$t1, 0($s1)			# -
	sw	$t2, 4($s1)			# -
	sw	$t3, 8($s1)			# -
	sw	$t4, 12($s1)			# -
	sw	$t5, 16($s1)			# -
	sw	$t6, 20($s1)			# -
	sw	$t7, 24($s1)			# -
	sw	$t8, 28($s1)			# - 
	sw	$t9, 32($s1)			# -
	sw	$s7, 36($s1)			# -
	sw	$s6, 40($s1)			# -
	addi	$sp, $sp, 44			#
getX:						# 
	li	$v0, 4				# "Enter your x value" prompt
	la	$a0, xPrompt			# -
	syscall					# -
	li 	$v0, 5				# xValue = Keyboard.nextInt();
	syscall					# -
	move	$s2, $v0			# -
	li	$s3, 0				# cycleCount = 0;
evaluatePolynomial:				#
	li	$a2, 0				#
	jal	returnXtotheN			# 
	beq	$s3, $s0, resetX		# if (cycleCount == nDegree)
	add	$s3, $s3, 1			# cycleCount += 1;
	j	evaluatePolynomial		#
returnXtotheN:					#
	beq	$s3, 0, returnXtotheZero	# if (cycleCount == 0)
	beq	$s3, 1, returnXtotheOne		# if (cycleCount == 1)
	beq	$s3, 2, returnXtotheTwo		# if (cycleCount == 2)
	beq	$s3, 3, returnXtotheThree	# if (cycleCount == 3)
	beq	$s3, 4, returnXtotheFour	# if (cycleCount == 4)
	beq	$s3, 5, returnXtotheFive	# if (cycleCount == 5)
	beq	$s3, 6, returnXtotheSix		# if (cycleCount == 6)
	beq	$s3, 7, returnXtotheSeven	# if (cycleCount == 7)
	beq	$s3, 8, returnXtotheEight	# if (cycleCount == 8)
	beq	$s3, 9, returnXtotheNine	# if (cycleCount == 9)
	beq	$s3, 10, returnXtotheTen	# if (cycleCount == 10)
returnXtotheZero:				#
	lw	$t1, 0($s1)			# 
	add	$s4, $s4, $t1			# polyResult += coefficient_0;
	jr	$ra				# 
returnXtotheOne:				# 
	lw	$t1, 4($s1)			# 
	mul	$t2, $t1, $s2			# y = coefficient_1 * pow(xValue, 1);
	add	$s4, $s4, $t2			# polyResult += y;
	jr	$ra				# 
returnXtotheTwo:				# 
	lw	$t1, 8($s1)			#
	mul	$t2, $s2, $s2			# y = coefficient_2 * pow(xValue, 2);
	mul	$t2, $t2, $t1			# -
	add	$s4, $s4, $t2			# polyResult += y;
	jr 	$ra				#
returnXtotheThree:				# 
	lw	$t1, 12($s1)			#
	mul	$t2, $s2, $s2			# y = coefficient_2 * pow(xValue, 3);
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $t1			# -
	add	$s4, $s4, $t2			# polyResult += y;
	jr 	$ra				#
returnXtotheFour:				# 
	lw	$t1, 16($s1)			#
	mul	$t2, $s2, $s2			# y = coefficient_2 * pow(xValue, 4);
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $t1			# -
	mul	$t2, $t2, $s2			# -
	add	$s4, $s4, $t2			# polyResult += y;
	jr 	$ra				#
returnXtotheFive:				# 
	lw	$t1, 20($s1)			#
	mul	$t2, $s2, $s2			# y = coefficient_2 * pow(xValue, 5);
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $t1			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	add	$s4, $s4, $t2			# polyResult += y;
	jr 	$ra				#
returnXtotheSix:				# 
	lw	$t1, 24($s1)			#
	mul	$t2, $s2, $s2			# y = coefficient_2 * pow(xValue, 6);
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $t1			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	add	$s4, $s4, $t2			# polyResult += y;
	jr 	$ra				#
returnXtotheSeven:				# 
	lw	$t1, 28($s1)			#
	mul	$t2, $s2, $s2			# y = coefficient_2 * pow(xValue, 7);
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $t1			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	add	$s4, $s4, $t2			# polyResult += y;
	jr 	$ra				#
returnXtotheEight:				# 
	lw	$t1, 32($s1)			#
	mul	$t2, $s2, $s2			# y = coefficient_2 * pow(xValue, 8);
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $t1			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	add	$s4, $s4, $t2			# polyResult += y;
	jr 	$ra				#
returnXtotheNine:				# 
	lw	$t1, 36($s1)			#
	mul	$t2, $s2, $s2			# y = coefficient_2 * pow(xValue, 9);
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $t1			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	add	$s4, $s4, $t2			# polyResult += y;
	jr 	$ra				#
returnXtotheTen:				# 
	lw	$t1, 40($s1)			#
	mul	$t2, $s2, $s2			# y = coefficient_2 * pow(xValue, 10);
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $t1			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	mul	$t2, $t2, $s2			# -
	add	$s4, $s4, $t2			# polyResult += y;
	jr 	$ra				#
resetX:						# 
	li	$v0, 4				# System.out.println("The result of your polynomial is " + polyResult);
	la	$a0, resultPrompt		# -
	syscall					# -
	li	$v0, 1				# -
	sw	$s4, polyResult			# -
	lw	$a0, polyResult			# -
	syscall					# -
	li 	$v0, 4				# "Would you like to choose a new X?" Prompt 
	la	$a0, newXPrompt			# -
	syscall					# - 
	li	$v0, 5				# answer = Keyboard.nextInt(); 
	syscall					# - 
	move	$t1, $v0			# - 
	beq	$t1, 0, newPolynomial		# if (answer == 0) 
	li	$s2, 0				# xValue = 0; 
	j	getX				# 
newPolynomial:					# (resetCoefficients/resetDegree subroutine included here)
	li	$v0, 4				# "Would you like to evaluate a new polynomial?" prompt
	la	$a0, newPolyPrompt		# - 
	syscall					# - 
	li	$v0, 5				# answer = Keyboard.nextInt(); 
	syscall					# - 
	move	$t1, $v0			# - 
	beq	$t1, 0, theEnd			# if (answer == 0)
	li	$s3, -1				# cycleCount = 0;
	li	$s4, 0				# polyResult = 0;
	j	getDegree			# 
nError:						# 
	li	$v0, 4				# "Invalid degree of n" Prompt 
	la	$a0, nErrorPrompt		# -
	syscall					# -
	j	getDegree			# 
theEnd:						# 
	li	$v0, 10				# Exit
	syscall					# -
	
